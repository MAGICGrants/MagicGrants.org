---
layout: post
title: "The Road to Divisors in Monero"
excerpt: "What do you do when experts disagree? Three independent reviews, two years of work, and now a machine-checked proof"
date: 2026-09-29
author: magicboard
---

In May 2022, Liam Eagen [posted a preprint research paper on divisors](https://eprint.iacr.org/2022/596). This paper introduced an efficient way to prove elliptic curve scalar multiplications inside a zero-knowledge proof, which caught the eye of Monero developers. Luke Parker used this divisors scheme in [their Monero FCMP++ specification](https://github.com/kayabaNerve/fcmp-plus-plus-paper/blob/develop/fcmp%2B%2B.pdf) for the discrete log proof.

It would be possible for Monero to implement FCMP++ without this divisors technique, but the resulting protocol would be significantly less efficient, to the point of potentially being non-viable.

Unfortunately, Eagen did not provide convincing security proofs for their scheme. Thus, the Monero community (with the help of MAGIC Grants) embarked on a journey to sufficiently ensure the security of this technique.

Getting proofs for an existing idea may sound like a relatively simple and straightforward task. Instead, it became a complicated process that involved three research firms and took two years. We learned a lot along the way.

Today, three independent security firms have deemed Monero's use of this divisors scheme secure. The Monero community can therefore use it with confidence, knowing that it has undergone substantial review by multiple leading experts in this field. MAGIC Grants assisted with contracting two of the three firms.

Most recently, zkSecurity went a step further. They produced a [machine-checked proof](https://github.com/zksecurity/eagen-divisor-formalization) of the core soundness theorem in the Lean 4 proof assistant. This formalization is entirely zkSecurity's own work. We cover what it does and does not establish further below.

## What Divisors Do

Monero FCMP++ transactions prove that the output they spend exists somewhere in the entire history of the chain, rather than hiding among a small set of decoys. To do this efficiently, FCMP++ uses [Curve Trees](https://eprint.iacr.org/2022/756). Curve Trees require proving elliptic curve scalar multiplications inside a zero-knowledge proof. The straightforward approach emulates the curve arithmetic step by step inside the proof, which is expensive.

Eagen's technique takes a shortcut. Instead of computing the group operations inside the proof, the prover supplies a function on the curve whose zeros are the points being added. A classic result in algebraic geometry says that such a function exists exactly when those points sum to zero. The verifier then checks this function at randomly chosen points using a logarithmic-derivative identity. In Parker's FCMP++ gadget, this verifies a multi-scalar multiplication with only a handful of constraints.

The central security question is **soundness**: can a dishonest prover submit a function that passes the random check even though the claimed equation is false? If so, an attacker could potentially prove false statements inside FCMP++. Of course, this would be disastrous.

## Initial Research Project

We conducted a competitive bidding process for the first stage of the review. Our intent at the time was for one firm to write the majority of the security proofs, and for another firm to review them and verify that they were correct. We selected Veridise to write the initial proofs.

Veridise described the scope in their proposal as follows:

> Veridise will provide mathematical consulting services for the client. These services involve creating either a proof of soundness or counterexample for equation (1) shown in Liam Eagen's paper "Zero Knowledge Proofs of Elliptic Curve Inner Products from Principal Divisors and Weil Reciprocity."

The contract also included a "bonus" conditioned on a complete soundness proof or valid counterexample.

Unfortunately, this scope was probably not specific enough to sufficiently support the use of the divisors scheme in Monero. Cypher Stack, which reviewed Veridise's work, did not find the proofs convincing. Veridise maintained that their work was correct, and they suggested additional projects to provide supporting documentation to this effect.

MAGIC Grants does not take a position on this disagreement.

## Subsequent Research Projects

Ultimately, this disagreement between the two firms led to additional work by both Veridise and Cypher Stack. Veridise completed two more projects to further investigate negative coefficients and logarithmic derivatives, and to further support their approach.

Cypher Stack, outside of an agreement with MAGIC Grants, decided to independently justify a different scheme, SLVer Bullet. Through this alternative work, Cypher Stack agreed that the originally proposed design was effectively equivalent and could be used securely.

## Third Review

Given the complexity of the situation and the disagreement between firms, the Monero community expressed a desire during a Monero Research Lab (MRL) meeting for a third independent review. One could argue that this third review was not *strictly* necessary, since the two prior firms at this stage agreed that it was safe for Monero to use the divisors technique (though they disagreed on the supporting reasons). Luckily, the Monero community had the resources to support a third review, so it was considered prudent. The community selected zkSecurity to perform this review.

Given the difficulty of getting to this point, MAGIC Grants negotiated an "all-inclusive" quote with zkSecurity. To receive payment, zkSecurity would need to either provide evidence that sufficiently supported the security of divisors, or demonstrate that divisors were insecure in a way that could not be rectified. This structure was intended to prevent minor changes, disagreements, or partially completed work from causing (further) substantial delays.

Ultimately, zkSecurity also agreed with the suitability of Eagen's divisors scheme for Monero. Their [Notes and Proofs for Divisor Techniques](https://blog.zksecurity.xyz/posts/divisor-notes/), written by Mathias Hall-Andersen and Diego F. Aranha, are self-contained. They include a new proof of extraction and more precise definitions of the relations being proven. They also give a formal treatment of how the interactive protocol composes with a non-interactive proof system, and they carry the analysis down to the R1CS verifier circuit used by Parker's gadget.

With all three firms agreeing that divisors are safe to use, we believe that Monero can use them with confidence.

## A Note About One zkSecurity Recommendation

zkSecurity suggested a minor modification to the divisors scheme. Specifically, they discussed the check that prevents a prover from submitting a trivial all-zero function. Parker's FCMP++ gadget handles this with a single, cheap constraint: the prover's function must be normalized so that one specific coefficient equals 1. zkSecurity pointed out that a small fraction of legitimate functions cannot be normalized this way. In rare cases, this means an honest prover would be unable to produce a proof. As an alternative, zkSecurity described a hash-based check that works for every valid function. It costs one constraint and requires a fresh random value for each proof, making it slightly less efficient than Parker's approach.

Importantly, this is a *completeness* concern, not a *soundness* concern. It affects whether an honest user can always generate a proof, not whether a dishonest user can forge one. The affected cases should be negligible, and they can only rule out certain choices of randomness, never a specific output. In other words, this cannot make any output unspendable; a wallet that hits one of these cases can simply choose different randomness. zkSecurity's analysis, and their later Lean formalization, prove soundness for any such check that rules out the all-zero function, including the one Parker uses.

We are grateful for this recommendation, but we believe that updating the protocol at this stage would cause more harm than benefit. Switching to a different check would change the circuit, which has [already been reviewed by Veridise](https://magicgrants.org/2025/08/05/Veridise-Gadgets-Circuit) (and is undergoing a second review), and the implementation, which has been [audited by Trail of Bits](https://magicgrants.org/2026/08/17/Monero-FCMP-Cryptography-Implementation-ToB). Those changes would need fresh review. In return, it would only remove a negligible chance of an honest proof failing, and it would not improve soundness.

## The Latest Development: zkSecurity's Formal Verification

After completing their notes, zkSecurity kept working on their own. zkSecurity's Mathias Hall-Andersen formalized the central soundness argument in the Lean 4 proof assistant, where a computer checks every step of the argument. The work spanned roughly five months and more than 1,100 commits.

### What zkSecurity Proved

In plain terms, zkSecurity's Lean proof shows that a cheating prover cannot get a false claim past the divisor check, except with a tiny, precisely calculated probability (far less likely than guessing a 12-word seed phrase). Lean checked every step of this argument, mechanically confirming the central result of the written proofs.

This holds no matter what the prover sends; the proof does not assume the prover is honest. It also covers both the specific variant Parker uses in FCMP++ and Eagen's original.

The proof is checked by Lean's kernel. It uses only Lean's three standard foundational axioms. Unlike the pen-and-paper notes, the main theorem avoids Hasse's theorem and uses explicit point-count hypotheses instead. zkSecurity also formalized completeness results, which show that honest provers are rarely rejected.

zkSecurity also took care to prevent the proof from being "gamed." The official theorem statements are frozen in a separate file. An independent judge, [leanprover/comparator](https://github.com/leanprover/comparator), runs on every change. The judge confirms that the proven theorems match the frozen statements exactly. It also confirms that no unapproved axioms were used, and it replays the full proof through a fresh kernel.

### What Formal Verification Tells Us

We already considered divisors secure for Monero before this formalization, based on the agreement of three firms. The formalization does not change that conclusion. What it adds is an extra layer of assurance: for the core argument, we no longer need to rely as much on human reviewers having caught every error.

Much of the project difficulty described above came from qualified experts disagreeing about whether a proof was convincing. A proof assistant has no comfort level. It either accepts every step or rejects the proof. For the core soundness claim, reviewers no longer have to trust that a long counting argument has no gaps.

We recently [wrote about an issue](https://magicgrants.org/2026/09/22/Bulletproofs+-Report) with the Bulletproofs+ aggregate range proof. An earlier audit noticed a problem in the relevant proof, but it did not fully write out the repair and instead said the result follows. With a machine-checked proof, it is harder to skip steps like that.

### What Formal Verification Doesn't Tell Us

Formal verification does not mean that Monero's implementation is perfect.

First, it only proves exactly what is stated. The definitions of the protocol, the relation, and the extractor are part of the theorem statement. Formal verification settles whether a proof is correct. It does not settle whether the statement is fit for purpose. Reviewers still need to read the statement and confirm that it matches what Monero actually does. This gap has caused real failures: the [Frozen Heart vulnerabilities](https://blog.trailofbits.com/2022/04/15/the-frozen-heart-vulnerability-in-bulletproofs/) allowed forged proofs in several Bulletproofs implementations because the protocol as specified hashed less than the security proof assumed.

Second, it covers only the interactive protocol with truly random challenges. Monero uses a non-interactive version. In that version, challenges are derived by hashing (the Fiat-Shamir transformation), and the divisor check runs inside the outer proof system (Generalized Bulletproofs). zkSecurity's notes prove this composition on paper, but this is outside the scope of the Lean formalization. Fiat-Shamir is a common source of real-world bugs, as zkSecurity [recently explained](https://blog.zksecurity.xyz/posts/fiat-shamir/).

Third, it does not cover the circuit or the code. The formalization does not verify how the check is arithmetized into constraints, and it does not verify the Rust implementation. It also does not cover the rest of FCMP++, including Curve Trees, spend authorization, linkability, and the choice of curves. Privacy, zero-knowledge, and side channels are also outside its scope. Other reviews, including Veridise's [review of the FCMP++ gadgets and circuit](https://magicgrants.org/2025/08/05/Veridise-Gadgets-Circuit) and Trail of Bits' [audit of parts of the cryptography implementation](https://magicgrants.org/2026/08/17/Monero-FCMP-Cryptography-Implementation-ToB), have covered many of these components. Many cryptocurrency projects ([including Monero](https://www.getmonero.org/2017/05/17/disclosure-of-a-major-bug-in-cryptonote-based-currencies.html)) have been vulnerable due to implementation flaws.

Finally, it relies on a small but nonzero trusted base. That base includes the Lean kernel, Mathlib and the supporting libraries, and the build tooling.

No single layer of review is sufficient on its own, and formal verification does not replace audits. Divisors now have an original paper, three independent reviews, circuit-level and implementation audits, and a machine-checked proof of their central soundness theorem. Together, these make the mathematical core of this part of FCMP++ one of the most thoroughly scrutinized components of the upgrade.

## Lessons Learned

The resources that the Monero community and MAGIC Grants expended on divisors should make clear that security is the top priority. It would have been unacceptable for Monero to deploy this technique without sufficient supporting evidence.

With the gift of hindsight, we could have approached this process better.

First, we should not have assumed that getting from *probably* secure to *definitely* secure would be a relatively straightforward task. It was not.

Second, we should not have assumed that different researchers would have similar comfort levels and approaches for determining whether a protocol is reasonably secure for deployment. Even when potential issues were raised, there were disputes about whether they applied at all and about how to address them. We now have a better idea of the level of review that is necessary for more widespread academic acceptance.

Third, when soliciting the initial proof construction proposals, we should have been clearer up front about our requirements and expectations for these proofs. One challenge was that we did not want to prescribe a specific method to the cryptographers. We wanted them to be able to justify Monero's usage by whatever means they felt were the most convincing and simplest to prove. We should have been clearer that the proofs would need to be reviewed by others and pass scrutiny. This was difficult to balance against our desire to avoid an overly expensive exercise of making the content ready for research-paper publication.

We believe that we have incorporated these lessons throughout the divisors review process, and we have continued to apply and improve upon them in our other review programs.

## Special Thanks

MAGIC Grants would like to thank Veridise and zkSecurity for their work with us on these projects. We would also like to thank Cypher Stack for their contributions in this same area, and their longtime support for the Monero community.

We especially thank zkSecurity and Mathias Hall-Andersen for investing substantial effort in the Lean formalization and publishing it openly. We also thank Diego F. Aranha for his work on the divisor notes, Liam Eagen for the original research, and Luke Parker for developing FCMP++. Finally, we thank the Monero community donors who funded these reviews.

MAGIC Grants is a 501(c)(3) public charity that supports public cryptocurrency infrastructure, including security audits and reviews.

## Documents

Below is a list of documents that relate to the divisors technique. MAGIC Grants was not directly involved in the creation of all of these documents.

### Eagen

[2022-05 Original Paper](https://eprint.iacr.org/2022/596 "Zero Knowledge Proofs of Elliptic Curve Inner Products from Principal Divisors and Weil Reciprocity"){: .btn-secondary}
{: .btn-list}

### Veridise

These documents by Bassa were produced to further substantiate Eagen's approach:

[2024-06 Soundness Proof](/files/2024-06-23-veridise-monero-proof.pdf "Soundness Proof for Eagen's Proof of Sums of Points"){: .btn-secondary}
[2024-08 R1CS Gadget Notes](/files/2024-08-08-veridise-monero-gadget.pdf "Notes on the R1CS Gadget for Providing Discrete Logarithm Proofs"){: .btn-secondary}
[2024-11 Logarithmic Derivatives](/files/2024-11-09-veridise-monero-logarithmic-derivatives.pdf "On the Use of Logarithmic Derivatives in Eagen's Proof of Sums of Points"){: .btn-secondary}
[2025-02 Discrete Log Soundness Proof](/files/2025-02-14-veridise-monero-soundness.pdf "Soundness Proof for an Interactive Protocol for the Discrete Logarithm Relation"){: .btn-secondary}
{: .btn-list}

These documents were produced by Veridise in response to Cypher Stack's SLVer Bullet paper:

[2025-07 Response to DL Gadget Review](/files/2025-07-11-Cypher_Stack_Response.pdf "Response to 'A Further Review of the DL Gadget Of Interest' by Goodell, Salazar, Slaughter, Szramowski"){: .btn-secondary}
[2025-07 SLVer Bullet Review](/files/2025-07-11-SLVer_Bullet_Annotated.pdf "Results of a First Review of 'SLVer Bullet: Straight-Line Verification for Bulletproofs' by Goodell, Salazar, Slaughter, Szramowski"){: .btn-secondary}
[2025-07 log_deriv PDF](/files/2025-07-11-log_deriv.pdf){: .btn-secondary}
[2025-07 log_deriv Notebook](/files/2025-07-11-log_deriv.ipynb){: .btn-secondary}
{: .btn-list}

### Cypher Stack

These documents are by Goodell, Salazar, Slaughter, and Szramowski:

[2025-03 Soundness Review](https://github.com/cypherstack/divisor_deep_dive/blob/main/pdfs/sum_of_points.pdf "A Review of Soundness of Divisors-based Proofs"){: .btn-secondary}
[2025-05 DL Gadget Review](https://github.com/cypherstack/divisor_deep_dive/blob/main/pdfs/follow_up.pdf "A Further Review of the DL Gadget Of Interest"){: .btn-secondary}
[2025-06 SLVer Bullet](https://github.com/cypherstack/divisor_deep_dive/blob/main/pdfs/silverbullet.pdf "SLVer Bullet: Straight-Line Verification for Bulletproofs"){: .btn-secondary}
{: .btn-list}

### zkSecurity

[2026-04 Notes and Proofs](/files/2026-04-27-zksecurity-notes-and-proofs-for-divisor-techniques.pdf "Notes and Proofs for Divisor Techniques"){: .btn-secondary}
[2026-08 Lean 4 Formalization](https://github.com/zksecurity/eagen-divisor-formalization "Formalization of Eagen's ECIP Proof"){: .btn-secondary}
{: .btn-list}
