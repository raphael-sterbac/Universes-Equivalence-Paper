
- (l8) "algorithmic proof": What does it mean for a proof to be algorithmic? Do you mean constructive?

- (l20) "Martin-Löf Martin-Löf [15], Martin-Löf [16]". (Although I'm not a fan of using LLMs for writing conference articles, they are certainly very good at finding and correcting small errors like this one, so consider using one for such administrative corrections.)

- "When presenting Type Theory in an algebraic fashion, Tarski universes are essential, at least if we do not want to introduce sort equations" : Like you say, Russell universes are really not a problem when using sort equations, so it could be good to explain more why sort equations are considered problematic.

- (l45) "the corresponding implicit theories actually implemented in proof systems": Even thought the implementation of proof assistants use implicit non-annotated syntax, this does imply that the underling implemented theories are themselves implicit. In fact, it is possible to justify algorithms that operate only on non-annotated syntaxes (not only for typing, but also for conversion checking) wrt theories that are fully annotated. The middleman role played by the non-annotated system is thus removed, we are left only with the fully annotated system and the non-annotated implementation. We do this for instance in our last paper with Théo (Secs 4 and 5 of https://doi.org/10.1145/3828691), but there are also other references (for instance, sec 3.2.2 of https://www.danielgratzer.com/papers/type-theory-book.pdf, although there conversion is still fully annotated). In any case, this is just one possible approach, and I'd argue that connecting explicit and implicit theories is also valuable for understanding the links between papers in the literature, specially given that in the past implicit syntax was the norm.

- (related work) There is an subtle issue here. The paper [3] of Assaf handles "simple" cumulativity, without covariance, and that paper is actually correct. The proofs that are incorrect are the ones in Assaf's and Thiré's ([21]) thesis and they concern cumulativity *with covariance*, and this is the problem our paper with Théo solves. The related work section of our paper describes this and the problems in detail. You also say that our proof uses the same technique as Thiré and Assaf, but actually our technique is based on Streicher's (the only reason we don't cite his thesis is because at the time I didn't know he was the one would devised the technique..., instead we cited a later paper that also used it). The errors in Thiré and Assaf come from their attempt to define the translation function directly, instead of reasoning over its i
- (l213) I suggest you to insist more here on the difference between explicit and implicit substitutions: in the previous section, the notation tσ was a node of the term syntax for every term t and substitution σ, whereas here tσ denotes a meta-operation that takes a term and a substitution to another term. It would also be good to say more explicitly what is your grammar of substitutions here.

- (figs 2 and 3) I guess you forgot the condition that Gamma is well-formed in some of the rules (without it, this contradicts Lem 21). You also never introduce the typing judgement for contexts.

- (l244) You don't say what it means for a substitution to be "elementary", is this a formal definition or just an informal qualifier?

- The "strip" and "fold" notations are a bit long, why not something like ‖t‖ or [t] or  \llbracket t \rrbracket?

- (def 13) Formatting problem on the clause for Pi. 

- (def 13) A very important point here: you keep the annotation of the lambda and this is *essential* for proving the equivalence Russell <-> PTS without normalisation. I have made a related observation in https://dl.acm.org/doi/pdf/10.1145/3828691, see Remark 4.1 there. The counter-example uses a result by Thierry and Gilles Barthe, and comes from the fact that in the system with type-in-type you can define a family of looping combinators that are equal when erasing annotations, but non-convertible when considering annotations. (Update: I now see that a related remark appears at the end of sec 6. But note that the counterexample there does not really work because the theory has normalization, you really need to go to a non-normalizing theory to have a real counterexample)

- IMO, the equivalence GAT <-> Tarski would deserve a more detailed discussion:
  - First of all, it would be important to say explicitly somewhere that your GAT presentation is extrinsic (most people use the intrinsic reading nowadays), which is needed to define the map GAT -> Tarski. Therefore, in sec 2 whenever you write t = u you don't mean meta-level equality, but rather a conversion relation. This point was not clear to me when first reading that section.
  - A related point is that you could insist on the fact that the operations given in sec 3.2 are defined over the raw untyped syntax, not over well-typed terms.
  - As you say, you gloss over the fact that the operations in the GAT have one annotation more, namely the context.
  - The fold operation could also be explained a bit more. You say that it is defined inductively, but inductively on what? On the grammar of raw GAT terms? But the operations [a] and sigma^+ are not part of the syntax, they are derived (def 5). In the clause for fold(A sigma) you also don't explain the relation between sigma and sigma_1..sigma_n. Finally, what is the symbol @ here?
  - The lemmas of sec 4 could be more detailed (see my other comments below).

- (lem 15) What do you mean exactly by "fold is well-defined"? You could write the statement being proved more explicitly.

- (lem 16) Has this notation "α: ∆ →Γ" been introduced?

- (lem 17) It would be good to illustrate at least one case of the verification that this preserves the equations.

- (Thm 19) "Each rule of TTarski is trivially admissible of TGAT" : I think this deserves a more detailed explanation.

- (lemmas 21 and 22) Maybe a more uniform way of stating these is that (A) Gamma |- A type => |- Gamma ; (B) Gamma |- t : A => Gamma |- A type ; (C) Gamma |- t_1 = t_2 : A => Gamma |- t_i : A (i=1,2). This is sometimes called presuppositivity, or boundary condition.

- (lemma 24) As a side remark, the discussed technicality in the statement also appears in our case, see thm 26 there. Also note that, in point 3, A_0 = A_1 is implied by u_0 = u_1 : A_0. Indeed, from u_0 = u_1 : A_0 we get u_1 : A_0 and hence A_0 = A_1 by uniqueness of types.

- (l565) "non-convertible derivations" : What does it mean for derivations to be convertible?

- (sec 7) It is not clear if what is said in this sec is purely an informal proof sketch, or if this is describing an actual proof written or formalized elsewhere.

