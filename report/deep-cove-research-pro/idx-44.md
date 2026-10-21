# LCvx, SCvx, and GuSTO: Autonomous-Vehicle Trajectory Generation Through 2022

**Convex optimization offers practical onboard advantages.** Optimization-based trajectory generation computes a vehicle’s motion and control inputs while satisfying dynamics, actuator limits, and mission constraints. Convex formulations are attractive because their numerical solution is comparatively reliable and computationally predictable, although the complete guidance algorithm must still fit the onboard processing budget. Through **31 December 2022**, the main distinction is that Lossless Convexification (LCvx) can preserve the original global optimum for particular structured problems, whereas Successive Convexification (SCvx) and Guaranteed Sequential Trajectory Optimization (GuSTO) address broader nonlinear problems through successive local approximations and conditional convergence guarantees. [1]

**The application record is already substantial.** LCvx has especially clear rocket-flight evidence through G-FOLD on **Masten Space Systems’ Xombie**. SCvx has demonstrated quadrotor trajectory generation in flight, alongside extensive rocket-landing simulations. GuSTO has both numerical results and a ground hardware demonstration on a free-flying spacecraft-robot testbed at Stanford. These represent different forms of validation, not interchangeable deployment milestones. [2][3]

**The survey follows the engineering questions.** After a brief explanation of trajectory optimization and onboard computation, each algorithm is examined through its mechanism, advantages, boundaries, and documented applications. A final comparison separates mathematical guarantees, computational evidence, and suitability for landers, drones, and other robots.

| Algorithm | Main mechanism | Particularly suitable problems | Solution guarantee | Concrete evidence by 2022 |
|---|---|---|---|---|
| LCvx | Exact relaxation of eligible nonconvex constraints | Structured fuel-optimal powered descent | Original optimum preserved under losslessness conditions | Masten Xombie rocket flight tests |
| SCvx | Repeated local convexification with safeguards | Nonlinear dynamics, free final time, conditional constraints | Formulation-dependent convergence and stationarity | Quadrotor flight demonstrations; rocket simulations |
| GuSTO | Continuous-time sequential convex programming | Control-affine robots with collision and goal constraints | Pontryagin-stationary limits under assumptions | Stanford free-flyer ground experiment; simulations |

The mechanisms and guarantees in this table come from the G-FOLD formulation [5], the 2016 SCvx analysis , and the 2019 GuSTO paper .

## Optimization-based trajectory generation and onboard computation

### What trajectory optimization computes

**A trajectory includes motion and timing.** A geometric path says where a vehicle should travel; a dynamically feasible trajectory also specifies when it reaches each state and what inputs produce that motion. Optimization-based trajectory generation chooses the state history—such as position, velocity, attitude, and mass—and the corresponding control history to minimize a performance criterion.

**The standard formulation is optimal control.** In compact notation, the decision variables are a state trajectory \(x(t)\), a control trajectory \(u(t)\), and sometimes the final time \(t_f\). A representative formulation is:

\[
\min_{x(\cdot),u(\cdot),t_f}\ J=\phi(x(t_f),t_f)+\int_0^{t_f}L(x(t),u(t),t)\,dt
\]

\[
\dot{x}(t)=f(x(t),u(t),t),\qquad x(0)=x_0,\qquad x(t_f)\in M_f,\qquad x(t)\in X,\qquad u(t)\in U.
\]

Here, \(\phi\) is a terminal cost, \(L\) is a running cost, \(M_f\) is the permitted terminal or goal set, and \(X\) and \(U\) describe state and control restrictions.

**Mission objectives determine the useful trajectory.** A planetary lander might maximize remaining mass at touchdown, subject to engine-throttle limits and a safe approach corridor. A drone might minimize maneuver time or control effort while avoiding obstacles. A spacecraft robot might minimize effort while reaching any acceptable berthing configuration, rather than one prescribed terminal state.

| Vehicle context | Typical objective | Important states | Representative constraints |
|---|---|---|---|
| Planetary lander or landing rocket | Fuel use or landing error | Position, velocity, mass, attitude | Thrust bounds, pointing, glideslope, touchdown conditions |
| Drone or quadrotor | Time or control effort | Position, velocity, attitude | Thrust envelope, obstacles, passage geometry |
| Free-flying spacecraft robot | Effort and trajectory quality | Position, velocity, attitude, angular rate | Collision clearance, actuator bounds, terminal goal set |

These examples are represented in the powered-descent literature [7], quadrotor demonstrations [3], and GuSTO robot studies .

**Guidance and tracking play complementary roles.** The optimizer produces a planned motion and usually a nominal input sequence. A feedback controller then corrects tracking errors caused by disturbances, imperfect models, and actuator behavior. Optimization can occur once at the start of a maneuver or repeatedly as new state estimates arrive; repeated finite-horizon optimization is commonly called model predictive control, or MPC. The 2017 quadrotor demonstrations, for example, computed a translational trajectory onboard at maneuver onset and used closed-loop control to track it. [3]

**Onboard replanning addresses uncertain starting conditions.** For powered descent, atmospheric and parachute-phase uncertainties can leave a lander with a different position and velocity from those anticipated before flight. An optimizer starting from the current navigation estimate can recompute the divert and landing maneuver. Offline trajectories remain useful for initialization and testing, but a single precomputed nominal trajectory offers less adaptability when the actual descent state differs substantially. [5][8]

### Why convex optimization is attractive onboard

**Convexity removes nonglobal local minima.** A convex minimization problem has a convex objective and feasible set; in standard form, equality constraints are affine and inequality constraints have appropriate convex structure. Any local minimum is therefore a global minimum of that convex problem.

**Solver behavior becomes more predictable.** The aerospace literature emphasizes polynomial-complexity methods, well-defined numerical stopping conditions, and computational bounds for convex programming. These properties contrast with general nonconvex optimization, where poor initialization can cause divergence or convergence to an undesirable local solution, and the effort needed to establish a global optimum can be much greater. The advantage is not that every nonconvex solver is slow, but that convex formulations offer a more structured numerical task. [1]

**Conic structure matches common vehicle constraints.** Many useful constraints involve a Euclidean norm bounded by an affine expression—for example, an upper bound on thrust magnitude or a conical approach corridor. Such constraints fit second-order cone programming, abbreviated SOCP. An SOCP is a convex program built from affine relations and second-order cone constraints; it can be solved using mature interior-point methods. LCvx and many SCvx implementations exploit this structure. [9]

**Customization converts structure into speed.** A trajectory problem repeatedly presents similar matrix structures, changing mainly with the current state or reference trajectory. A customized solver can exploit that structure instead of treating every solve as an unrelated problem. Dueri and colleagues reported runtime reductions of two to three orders of magnitude in many applications of their customized interior-point methodology, illustrating why solver implementation matters alongside the convexification itself. [9]

**Limited computation favors controlled problem size.** Discretizing time converts a continuous trajectory into finitely many decision variables. More temporal nodes and richer models increase the optimizer’s freedom and fidelity, but also enlarge the numerical problem. For onboard use, the relevant design is consequently a combination of model, discretization, convexification, solver, and stopping conditions—not merely a choice of algorithm name. [7]

**The complete algorithm has two timescales.** A convex solver has its own iterations, while SCvx and GuSTO add an outer sequence of convexified trajectory problems. Predictable solution of one convex subproblem does not automatically establish a fixed deadline for the entire outer loop. A 2022 powered-landing study explicitly identified repeated SOCP solves as a major computational cost and noted that onboard CPU limitations can still obstruct real-time guidance. [8]

**The central distinction is therefore structural.** LCvx asks whether a particular nonconvexity can be removed exactly. SCvx and GuSTO ask whether the original problem can be approached through a well-managed sequence of tractable local models. Convex optimization is attractive onboard because it makes the numerical core dependable; the surrounding formulation determines whether that dependability extends to the original vehicle problem.

**Additional documented evidence**

Through 2022-12-31, onboard convex optimization helps when the formulation—not merely the solver—is convex: the model can have global-optimum properties, whereas sequential convexification is local. Nonconvexity comes from nonlinear dynamics, thrust geometry, obstacles, free time, and coupled constraints; relaxation and linearization trade exactness for model validity and discretization cost [26][32][39].

For road vehicles, landers, and drones, reliability means feasible replanning before the deadline; efficiency means processor/memory fit [23][29][32]. LCvx uses a bounded SOCP sequence and static-memory solvers; its 3-DoF guarantee is confined to a mission-design convex set and omits attitude/line-of-sight constraints [32]. SCvx and GuSTO use local convex subproblems, hard trust regions, and outer updates; a sequential-convexification landing case failed at \(w_{\mathrm{tr}}=10^{-3}\) [32].

In 2020 planar landing, hand parsing avoided redundant matrix construction and dynamic allocation; about 800 nonzeros were updated per SCP iteration, with expected cubic-in-\(N\) solver scaling. Less than 1% suboptimality took about 100 ms on a 3.2 GHz i5 with 8 GB RAM; a 2-norm trust region saved 11 ms per iteration in 100 trials, only in that case [32].

Fair comparison needs a baseline, metric/tolerance, hardware, horizon/nodes, solver, scale, and success criterion. In 2012, CMU tests used a 2.8-GHz i5-760 with 4 GB RAM at 8 Hz; finer grids lowered cost but lengthened planning [24]. A 2018 convex speed planner took 0.03–0.07 s per solve for 100 points and 0.05–0.2 s for 201 with Gurobi/Julia, but used proof-of-concept parameters [26]. No like-for-like ranking follows; zero-speed singularities, model mismatch, or noise can cause infeasibility [26][27].

Nonlinear dynamics, obstacles and nonzero thrust bounds make problems nonconvex; a convex solver cannot change that. Global optimality applies only to the convex model; LCvx exactness and SCvx feasibility/convergence remain conditional [30][25]. SCvx linearizes iterates into SOCPs; trust regions and penalized virtual control address infeasibility, but initialization/discretization remain risks [33][34]. Compare timings with context: G-FOLD (LCvx-related) reports 100 ms on a 1.4-GHz Pentium M [25]; a QCQP reports 10–12 ms for 30 nodes/~10 s on i7/8 GB, excluding perception [31]. Lander safety and drone power/collision constraints qualify gains [25][28]. GUSTO≠GuSTO: FPGA tool [41][42].

The evidence supports a conditional, not universal, reliability advantage: convexity can certify the global optimum of the stated convex model, but not automatically of the original nonconvex vehicle problem. Common nonconvexities are nonlinear dynamics, thrust/control geometry, obstacle or collision constraints, and free final time . LCvx is stronger only when its relaxation is lossless. A slack variable replaces a nonconvex control-norm lower bound with a convex set; under stated dynamics, cost, state, and control-geometry assumptions, maximum-principle analysis makes the relaxed solution globally optimal for the original problem [38][46]. Boundary activation and discretization can break that equivalence [38][45].

SCvx trades the one-shot guarantee for broader modeling. It linearizes dynamics and constraints around the current trajectory, solves a finite-dimensional convex subproblem, and uses penalties, virtual control, and a trust region: these suppress defects, prevent artificial infeasibility, and limit linearization error, respectively [36]. Convergence is local or assumption-dependent: the analyzed formulation requires a suitable initial point, LICQ and Slater, and a sufficiently large penalty weight to recover the original problem [36]. GuSTO also uses trust-region penalties and virtual control; its continuous-time analysis gives stationary-point/convergence results under assumptions, not unconditional feasibility .

Efficiency evidence is contextual. In a 2020 LCvx rocket-landing benchmark, ECOS on a 2.5-GHz i5-7200U, 8 GB RAM and 150 nodes took 1.8–3.9 s per solve, versus 73.1–566.8 s for direct MICP with Gurobi; several MICP cases exceeded 10 min [46]. This supports tractability against that baseline, not universal onboard speedup. A SCvx quadrotor report reached >8 Hz onboard and 11 iterations, versus about 16 for SQP and 75 for fmincon, but supplied no comparable timing . A 2022 Mars-entry simulation using MATLAB/YALMIP/MOSEK and 201 nodes reported 7 versus 34 iterations for r-SCP versus SCP, and 5.779 versus 16.89 s against GPOPS; it was not onboard [37]. Custom solvers can avoid dynamic allocation and exploit fixed structure, but scaling and cache effects can erase gains [35]. Thus lander and drone relevance is plausible; fair comparisons still require matching hardware, horizon, discretization, tolerance, solver, memory/latency target, and feasibility criterion [35][46].

LCvx: exact only under restricted reformulation; discretization may break equivalence [47]. SCvx: local SOCPs, trust regions and virtual control trade breadth for weaker guarantees [43]. Context-bound; not comparable: <15 Mars iterations [43]; quadrotor 36.5/122.2 ms ARM/Intel [44]. GuSTO: onboard metric absent [50].

SCvx linearization risks infeasibility; slack/trust help [48]

Reliability is conditional: LCvx can be exact for its thrust-relaxation class; SCvx solves local convex models and needs trust-region/penalty tuning. [40] Runtime claims require matched hardware, mesh and stopping rules. [40]

Under limited onboard compute, memory and latency, convex optimization offers autonomous vehicles a conditional advantage: LCvx needs one or a small bounded sequence of SOCPs, and static-memory SOCP solvers support real-time implementation in principle, improving workload predictability without guaranteeing it across formulations [32]. SCvx writes each convex subproblem as min cᵀz subject to Az=b and linear/second-order-cone membership; hand parsing removes parser overhead, redundant constraints and dynamic memory, while latency and solver workload still depend on horizon, discretization, nominal trajectory, solver formulation and implementation [32][31].

Reliability needs separate guarantee classes: LCvx is feasible and globally optimal almost everywhere only under Conditions 1–4 [45]. SCvx is a local sequential approximation that linearizes nonlinear dynamics and constraints and uses virtual control and trust regions; initialization and settings affect convergence, and a trust-region weight of 10−3 failed in the cited case, so onboard latency, memory and solver workload remain conditional on hardware, horizon, discretization, solver and tolerance [32][34][49].

Comparable efficiency claims should use the same problem and report runtime per solve, memory, iterations to a stated tolerance, hardware, solver, horizon and discretization against a named baseline; otherwise LCvx’s bounded-SOCP workload is not commensurate with SCvx’s sequential iterations. The evidence supports only problem-class-specific efficiency, not a universal LCvx–SCvx–GuSTO ranking, because SCvx can fail under poor settings and LCvx is restricted to a stated problem class [32][46].

## Lossless Convexification: LCvx

### Core idea and working principle

**LCvx preserves an eligible problem’s optimum.** Lossless Convexification replaces particular nonconvex constraints with convex ones and proves that the relaxed optimization still recovers an optimum satisfying the original constraints. This is stronger than simply approximating a nonconvex problem by a convenient convex surrogate. Its most established autonomous-vehicle application is fuel-optimal powered descent with nonconvex thrust-magnitude and pointing restrictions. [5]

**Minimum thrust creates a nonconvex set.** Consider a thrust vector \(T(t)\) constrained by:

\[
0<T_{\min}\leq \|T(t)\|_2\leq T_{\max}.
\]

The upper bound defines a convex ball, but the positive lower bound excludes the ball’s interior near zero. The remaining shell is nonconvex. Geometrically, averaging two permitted thrust vectors can produce a vector whose magnitude is below the permitted minimum. This is a physical engine restriction, not an incidental mathematical complication. [5]

**A slack variable lifts the controls.** LCvx introduces an additional scalar, here denoted \(\Gamma(t)\), and replaces the magnitude relation by:

\[
\|T(t)\|_2\leq \Gamma(t),\qquad T_{\min}\leq \Gamma(t)\leq T_{\max}.
\]

These are convex constraints in the enlarged control space. For the eligible pointing-constrained landing formulation, a condition of the form \(\hat n^\top T(t)\geq \Gamma(t)\cos\theta\) is also imposed, where \(\hat n\) is the reference pointing direction and \(\theta\) is the allowed deviation. [5]

**The relaxation deliberately enlarges feasibility.** The new constraints permit \(\|T\|_2<\Gamma\), including combinations that would not obey the original minimum-thrust requirement. Merely solving this relaxed problem is therefore insufficient. The essential LCvx result is a proof that an optimal solution lies on the appropriate boundary, satisfying \(\|T\|_2=\Gamma\), under the theorem’s assumptions.

**Optimal-control theory supplies that proof.** The G-FOLD account uses Pontryagin’s maximum principle: along an optimum, the control maximizes the relevant Hamiltonian expression. For the eligible relaxed control set, the maximizing controls occur at extreme points that also belong to the original nonconvex set. Because the relaxed problem contains the original feasible solutions and its optimum satisfies the original constraints, that optimum also solves the original problem. [5]

**Fuel accounting must remain physically consistent.** In the relaxed landing formulation, mass depletion is tied to \(\Gamma\), rather than directly to \(\|T\|_2\). Tightness of the relaxation makes the two descriptions agree at the optimum. This coupling explains why losslessness depends on the complete optimal-control formulation: objectives, dynamics, boundary conditions, and other constraints all matter. A slack variable alone does not establish exactness. [5]

**Variable changes address additional coupling.** A rocket’s acceleration depends on thrust divided by its changing mass. A common powered-descent formulation introduces logarithmic mass and thrust-acceleration variables. Using simplified point-mass notation, let \(z=\log m\), \(a=T/m\), and \(\sigma=\Gamma/m\). For constant gravity and proportional propellant consumption, the transformed relations take the form:

\[
\dot r=v,\qquad \dot v=g+a,\qquad \dot z=-\alpha\sigma,\qquad \|a\|_2\leq \sigma.
\]

These substitutions expose affine dynamics and a conic control relation, while the physical thrust bounds require their corresponding transformed treatment. The 2022 powered-landing study describes this combination of variable substitution and lossless relaxation explicitly. [8]

**Discretization produces an implementable program.** After reformulation, time is discretized and the finite-dimensional problem is assembled as an SOCP. For example, the 2022 study uses an equidistant trapezoidal scheme, obtaining an objective and constraints expressed through affine relations and second-order cones. A mature SOCP solver can then compute the trajectory. [8]

The practical sequence is:

1. Identify the nonconvex control structure covered by an applicable losslessness result.
2. Introduce lifting variables and any necessary changes of variables.
3. Formulate the relaxed problem while preserving the assumptions needed for exactness.
4. Discretize and solve the resulting convex program.
5. Recover physical controls and check the original constraints and trajectory representation.

**Losslessness and numerical accuracy are distinct.** An exact relaxation theorem concerns the relationship between mathematical problems. Numerical transcription, approximated thrust bounds, and a simplified vehicle model introduce separate errors. The 2022 implementation, for instance, explicitly retains a first-order thrust-bound approximation and reports a resulting systematic error. Calling its core relaxation lossless does not make every numerical approximation exact. [8]

### Advantages and suitable problems

**The strongest advantage is exactness.** For a covered problem, LCvx avoids the usual choice between a fast convex approximation and the optimum of the original nonconvex formulation. Once the equivalence is established and the remaining problem is convex, the optimizer can exploit global solution methods. For fuel-limited landing, this matters because excessive conservatism can unnecessarily reduce divert capability or payload margin. [5]

**A fixed-time solve is comparatively simple.** If terminal time and the required formulation parameters are supplied, the addressed nonconvexity does not require an outer sequence of local linearizations. The computation can reduce to solving one convex trajectory program. This removes a major source of runtime variability present in sequential methods, although a larger guidance system may still conduct searches or repeated replanning around that solve. [8]

**Powered descent provides a natural match.** LCvx is especially suitable when the main difficulty lies in minimum thrust and eligible pointing constraints, while translational dynamics and other restrictions can be expressed in a compatible form. Fuel-optimal soft landing, pinpoint landing, and large-divert guidance are its clearest examples. Glideslope and velocity bounds are valuable because they can often be retained as convex constraints rather than handled through further approximation. [5]

**The scope extends beyond basic landing.** The literature includes extensions to nonconvex control-bound and pointing constraints in soft landing, selected state-constrained linear systems, and maximal-divert trajectories with active velocity constraints. These broaden the useful class without turning LCvx into a general solution for arbitrary nonlinear optimal control. [9][10]

**Robotic flight can exploit the same structure.** The 2017 quadrotor experiments used LCvx to access a nonconvex portion of the control envelope and perform an agile flip maneuver. This is an important counterexample to the impression that LCvx is exclusively a rocket-landing technique: its applicability follows from the mathematical control structure, not from the vehicle’s industry or mission label. [3]

### Trade-offs and boundary conditions

**Eligibility is the principal restriction.** A nonconvex problem does not become losslessly convexifiable merely because it contains thrust limits. The applicable theorem must cover the way those limits interact with the dynamics, objective, state constraints, and terminal conditions.

**Final time can dominate the result.** In a fixed-final-time formulation, choosing an unsuitable duration can produce an infeasible trajectory, an invalid relaxed solution, or unnecessary propellant expenditure. The 2022 study shows that the useful final-time region can be narrow for particular initial conditions. Thus, global optimization at a supplied duration should not be confused with global optimization over all possible landing durations. [8]

**Free time adds an outer problem.** One established approach fixes the duration, solves the LCvx problem, and searches over duration using a one-dimensional procedure. Another introduces time as an optimization variable and uses successive convexification for the resulting nonlinear coupling. Both can require repeated SOCP solves. The distinction is practical: an exact inner relaxation can coexist with an iterative outer guidance algorithm. [8]

**Model simplicity has physical consequences.** The early G-FOLD formulation uses a point-mass model, decouples translational motion from attitude dynamics, and omits aerodynamic forces. Its Earth tests limited velocity to approximately \(27\ \mathrm{m/s}\), supporting the decision to treat aerodynamic effects as manageable disturbances in that regime. The same simplification is less persuasive when high-speed atmospheric flight, attitude-rate limits, or aerodynamic torques materially determine feasibility. [5]

**Fast attitude tracking is an assumption.** A translational optimizer can command a force direction that requires the vehicle to rotate. If an attitude controller can produce that rotation rapidly, the decomposition can work well. If rotation is slow or tightly constrained, a feasible translational trajectory may demand an unattainable attitude history. This is one reason full six-degree-of-freedom formulations became important in subsequent powered-descent work. [5][7]

**Practical implementations can remain suboptimal.** Wenzel’s 2017 DLR EAGLE study is instructive. Its guidance function used LCvx but overestimated optimal flight time throughout the reported simulation sets; the abstract describes fuel consumption approximately 20% above the optimal case in 80% of the sets. The source identifies the prototype as suboptimal, showing that a strong convex inner problem does not automatically make terminal-time selection or the complete guidance function optimal. [11]

### Applications and demonstrated results

**Masten Xombie is the clearest rocket example.** G-FOLD—Guidance for Fuel-Optimal Large Diverts—was developed by NASA’s Jet Propulsion Laboratory and the University of Texas at Austin. Its implementation literature explicitly identifies lossless convexification as the theoretical basis. Masten Space Systems supplied the XA-0.1B Xombie vertical-takeoff, vertical-landing rocket used to emulate planetary powered descent. [2][12]

| Algorithm | Project or study | Organization and vehicle | Application | Evidence level |
|---|---|---|---|---|
| LCvx | G-FOLD, 2012 flights | JPL/UT Austin; Masten Xombie | Large-divert landing | Flight tests; precomputed trajectories |
| LCvx | G-FOLD onboard campaign | JPL/UT Austin; Masten Xombie | Optimal powered descent | Eight flight tests; five onboard |
| LCvx | ADAPT, December 2014 | NASA/JPL; Masten Xombie | Vision-informed landing divert | Two autonomous onboard flight tests |
| LCvx | EAGLE study, 2017 | DLR EAGLE demonstrator | Fuel-optimal powered descent | Simulation |
| LCvx | Agile maneuvering, 2017 | University of Washington ACL quadrotors | Flip and obstacle avoidance | Onboard flight demonstration |
| LCvx | DNN-assisted study, 2022 | Tsinghua/Beihang powered-landing model | Terminal-time prediction and landing | Numerical and closed-loop simulation |

The rows are documented in the early G-FOLD report [5], onboard implementation study [2], NASA ADAPT report [12], EAGLE thesis [11], quadrotor paper [3], and 2022 DNN-assisted study [8].

**Early flights validated the planned motion.** The 2012 Xombie campaign, described in the AAS 13-386 report, used three trajectories generated offline and loaded onto the vehicle. The flights included diverts up to \(750\ \mathrm{m}\), with onboard feedback controlling translation and attitude. Their achievement was demonstrating that constrained, optimization-generated trajectories could be flown accurately; onboard trajectory optimization was the next stage. [5]

**Later campaigns demonstrated onboard optimization.** The implementation study reports eight flight tests, with guidance running onboard in near-real time on five flights using a customized interior-point solver. A related ADAPT conference report describes an approximately \(800\ \mathrm{m}\), fully three-dimensional, direction-reversing divert initiated at about \(290\ \mathrm{m}\) altitude; G-FOLD computed the trajectory onboard in approximately \(100\ \mathrm{ms}\). [2][13]

**Navigation integration advanced the demonstration.** NASA’s December 2014 ADAPT flights combined G-FOLD with the Lander Vision System, which estimated terrain-relative position by matching descent imagery against an onboard image. On 9 December, Xombie began changing course at roughly \(190\ \mathrm{m}\) altitude and reached a target pad \(300\ \mathrm{m}\) east. The significance is the closed loop from perception to position estimation to trajectory recomputation, operating onboard without human intervention. [12]

**EAGLE establishes a different evidence level.** Wenzel implemented a powered-descent guidance prototype for DLR’s EAGLE using the embedded conic solver ECOS. The assessment comprised two simulation sets, each containing 41,503 cases with different initial and final conditions. Typical computation on EAGLE’s onboard computer was expected to be below \(0.8\ \mathrm{s}\); that figure is a published onboard-computation expectation associated with the simulation study. [11]

**Quadrotor flights demonstrate cross-domain relevance.** Szmuk, Pascucci, Dueri, and Açıkmeşe’s 2017 IROS paper presents flight demonstrations on the Autonomous Control Laboratory’s custom quadrotors. LCvx enabled an agile flip, while lossless and successive convexification were combined for trajectories through a flight space containing keep-out zones. The optimizer generated three-degree-of-freedom translational trajectories, with feedback supplying the physical tracking. [3]

**A 2022 augmentation addressed terminal time.** The DNN-LCvx study used a deep neural network to predict landing duration, then solved one fixed-time LCvx SOCP. Its training data consisted of 20,000 SCvx-generated trajectories with 60 state/time pairs each: \(20{,}000\times60=1.2\) million samples. The predictor’s reported mean absolute timing error was \(11.6\ \mathrm{ms}\), and 99.11% of prediction errors were at most \(0.1\ \mathrm{s}\). [8]

**That augmentation changes the trade-off.** The study reported approximately \(5\)–\(8\ \mathrm{ms}\) per trajectory computation and a 12-fold speed improvement over its SCvx comparison in one example, using an Intel Core i7-10875H computer and ECOS. Those gains came with offline training, vehicle-specific retraining, and a restricted initial-state domain. The neural predictor is an augmentation around LCvx, not an additional losslessness theorem or a fourth algorithm in this survey. [8]

**LCvx is preferable when structure permits.** Its combination of exact relaxation, a comparatively simple convex solve, and rocket-flight evidence makes it highly attractive for compatible powered-descent problems; that preference changes when final-time selection or omitted dynamics becomes the dominant difficulty.

**Additional documented evidence**

**Lossless Convexification (LCvx)**

**Core result.** Lossless Convexification (LCvx, also written LCVX) replaces selected nonconvex control constraints with a convex relaxation; under formulation-specific conditions, the relaxed optimizer remains feasible for—and has the same optimum as—the original problem. “Lossless” therefore describes a proved exactness property for a problem class, not a guarantee that every nonlinear trajectory problem becomes convex [52][38].

**Principle and convex subproblem**

A representative LCvx problem is a finite-horizon optimal-control problem with state \(x(t)\), control \(u(t)\), continuous-time dynamics, an integral objective, an initial state, terminal conditions, and control constraints [52]. In planetary soft landing, a nonzero lower thrust bound together with an upper bound produces a nonconvex annular feasible-control set; in UAV path planning, upper and lower bounds on commanded-velocity magnitude produce the analogous nonconvexity [52][38].

LCvx introduces a slack variable to lift that nonconvex control set into a convex set. In the linear-system formulation, the cost and state constraints are convex, while the control set has the form \(U=U_1\setminus U_2\) for convex sets \(U_1\) and \(U_2\). The infinite-dimensional relaxed problem is then discretized into a finite-dimensional convex parameter-optimization problem [38]. For powered-descent guidance, the resulting problem is commonly expressed as a second-order cone program (SOCP); one or a small bounded sequence of SOCPs is sufficient for the described lossless formulations [32].

The method can also be extended beyond constant-gravity landing. The 2012 nonlinear-dynamics study applies LCvx to minimum-fuel soft landing with nonlinear gravity and aerodynamic drag and to UAV path planning with minimum- and maximum-velocity constraints [52]. Where the resulting finite-dimensional problem remains nonconvex because of general nonlinear dynamics, piecewise-linear approximations and mixed-integer linear programming (MILP) can recover a globally optimal solution of the approximated formulation; this is not the same as an ordinary single convex program for the original nonlinear dynamics [52].

**Exactness, assumptions, and guarantees**

The guarantee is conditional. In the nonlinear-control result, the theorem requires total observability of the relevant linearized costate pair over the horizon and a nonzero running-cost condition \(l(t,\Gamma)\ne0\) for every admissible control magnitude \(\Gamma\) and time \(t\). Under those conditions, the relaxed solution is globally optimal for the original nonconvex-control problem [52].

The earlier linear-system result requires controllability of \(\{A(\cdot),B(\cdot)\}\), the set condition \(U_2^\dagger=\{0\}\), an additional feasibility condition stated in the theorem, and—under the principal interior-state result—the relaxed state trajectory must remain in the interior of the feasible-state set, \(x(t)\in\operatorname{int}X\) throughout the horizon [38]. These assumptions explain why the result should be reported as conditional exactness rather than unconditional global optimality. Convex optimization can solve the relaxed problem globally under suitable computability and regularity assumptions, but that property transfers to the original problem only when the LCvx theorem applies [38].

Boundary trajectories require separate treatment. If the relaxed trajectory reaches the boundary of the state-feasible set, the main interior-state proof does not automatically apply; additional results or a two-step prioritized optimization are needed. The source reports an example in which failure of the hypotheses led to violated control bounds, while a boundary-case procedure restored losslessness elsewhere in the trajectory [38]. More generally, LCvx was characterized in the pre-2022 literature as applicable to a relatively narrow class of nonconvex problems, and some cited convexification formulations were restricted to fixed-final-time problems [33].

**Advantages and onboard-computation profile**

LCvx’s principal advantage is that it converts a difficult control-constraint geometry into a convex problem without sacrificing the original optimum when the exactness conditions hold. This gives global optimality for the stated model, computational tractability, and compatibility with receding-horizon model-predictive feedback [38]. For the 3-DoF powered-descent class, the reported advantages include a bounded SOCP workload and the availability of fast SOCP solvers using static memory allocation; solvability is guaranteed within a well-defined convex set that can be computed during mission design [32].

The implementation advantage is real but context-dependent. A 2014 embedded-SOCP study reports customized code with no dynamic memory allocation, reduced branching and unnecessary operations, and memory sized to the fixed problem structure; these features were intended for autonomous systems with limited computing capability [35]. In its planetary-landing benchmark, the customized solver was about **2 times faster** than the general Bsocp solver for small problems, gained almost no advantage at approximately **2,000 solution variables**, and was overtaken in scaling by ECOS above approximately **10,000 solution variables** [35]. These are benchmark results for particular solvers, discretizations, and problem sizes—not universal LCvx runtime or memory guarantees. The primary LCvx theoretical examples report computational tractability and polynomial-time solvability qualitatively, but do not provide a common onboard processor, solve-time, iteration-count, or memory denominator [38].

A related 2020 powered-descent study reports **less than 1% suboptimality** and runtimes of about **100 ms** on one **3.2 GHz Intel i5 core with 8 GB RAM**, but that case concerns a 6-DoF successive-convexification implementation rather than an LCvx-only solve; it should not be quoted as a direct LCvx benchmark [32].

**Suitability and limitations for autonomous vehicles**

LCvx is especially suitable when the dominant nonconvexity is a control-set feature such as a positive thrust lower bound, thrust pointing, or bounded commanded velocity, while the dynamics, state constraints, and objective can be represented in the required convex or exactly relaxable form. Documented classes include powered descent and planetary soft landing, state-constrained linear systems, nonlinear-gravity landing with suitable approximations, and UAV velocity-constrained path planning [52][32][38].

It is not a general substitute for trajectory optimization with arbitrary nonlinear dynamics, coupled attitude and translation, obstacle topology, or tightly coupled sensing constraints. A 3-DoF powered-descent LCvx trajectory models translation and thrust-vector-related constraints but not attitude dynamics; it therefore cannot by itself guarantee vehicle-mounted line-of-sight constraints. Even mild sensing constraints require extensive simulation against the full 6-DoF lander, and tightly coupled sensing and guidance may require hand-tuning and edge-case handling [32]. This boundary is important for drones as well: the pre-2022 LCvx evidence supports UAV path planning with velocity-norm constraints, but does not establish a general flight-certified LCvx planner for arbitrary drone environments [52].

**Documented applications through 2022-12-31**

- **Planetary soft landing, numerical examples — JPL/Caltech and NASA context, 2010.** The LCvx paper reports numerical soft-landing examples in which an autonomous spacecraft reaches a prescribed planetary location with zero relative velocity. The introduction places the mission context in robotic or crewed missions to Mars, the Moon, and asteroids; the work was performed at the Jet Propulsion Laboratory, California Institute of Technology, under contract with NASA. The evidence status is **numerical example**, not operational deployment; the source is a preprint submitted on **15 September 2010** [38].

- **Nonlinear-gravity soft landing and UAV path planning — publication and simulation study, 2012.** The LCvx extension demonstrates, in simulation, minimum-fuel planetary soft landing with nonlinear gravity and aerodynamic drag, and UAV path planning with minimum- and maximum-velocity constraints [52]. The source does not identify a company, named rocket, flight event, or deployed UAV; the supported status is **simulation/publication evidence**.

- **Mars powered-descent literature — 2007–2013.** The pre-2022 record includes *Convex Programming Approach to Powered Descent Guidance for Mars Landing* (2007), *Minimum-Landing-Error Powered-Descent Guidance for Mars Landing Using Convex Optimization* (2010), *Lossless Convexification of Powered-Descent Guidance with Non-Convex Thrust Bound and Pointing Constraints* (2011), and the 2013 soft-landing optimal-control paper [32]. These are method-specific research and guidance studies, but the cited evidence does not by itself establish operational deployment for each publication.

- **Related flight and onboard evidence — 2012–2014.** An embedded-SOCP paper reports real-time Mars-landing convex optimization validated in **three flights** onboard a NASA test rocket and lists a **650 m Xombie** divert test, first flight testing of real-time G-FOLD, and an ADAPT onboard large-divert demonstration with a reusable launch vehicle [35]. These records establish flight or onboard convex-guidance evidence, but the cited spans do not explicitly identify every flight implementation as LCvx; they are therefore **related or method-mapping-uncertain**, not verified LCvx deployments. No LCvx-specific card here establishes a company-owned rocket name.

Finally, a repository created on **29 April 2025** and a report dated **6 May 2025** use the project label **LCVX-PDG** and describe later Python/CVXPY simulations, including **500** or **1,000** Monte-Carlo trials and a reported **less-than-50-ms** laptop solve [55][56]. Those records are post-cutoff and are not used as evidence for the requested 2022 survey state; they also do not establish a company, named rocket, flight, deployment, or operational-use status.

LCvx uses slack SOCPs for nonconvex norm bounds; stated conditions give global optimality a.e.; applications: UAV paths, lander simulation [53][39].

LCvx (Lossless Convexification) uses a slack variable to turn nonconvex control-norm constraints into a convex problem; its documented Mars powered-descent formulation handles minimum/maximum thrust, speed, glideslope, and thrust-pointing limits [58]. LCvx is described as lossless and numerically efficient; pointing constraints serve onboard terrain-relative sensors, but no solve-time, iteration, memory, processor, or latency benchmark is reported [58]. LCvx is best supported for planetary powered descent/lander guidance, not a demonstrated drone case; its exactness is conditional on the stated formulation [58]. By 2022, LCvx records name no company, rocket/platform, flight or deployment status, or event date [58]. LCvx-related pre-2022 references list Mars minimum-error/convex-programming/pinpoint and Moon/Mars powered-descent works (2005–2010), but do not prove deployment; SpaceX is only an author affiliation [57]. Later 2024–2025 LCvx records are outside the 2022-12-31 cutoff and excluded [152,153].

LCvx’s 2010 evidence is simulation-only: 2.4-GHz, 4-GB MacBook Pro, 55 points; 14.3 s/23 iterations (case 1), 14.74 s/23 (case 2) [59].

DLR EAGLE’s LCvx prototype (2017) solved 41,503 cases in <80 ms on desktop and ~1 s on its onboard computer; evidence: simulation/PIL, not flight [60].

LCvx slack→SOCP for thrust; conditional global opt. a.e. [46]. Martian rocket: 1.8–3.9 s/solve vs MICP 73.1–566.8 [46]; KSP soft-landing feasible [62].

**Computational boundary, evidence, and applications**

LCvx best fits structured powered descent—planetary landing, fuel-optimal or minimum-error guidance, maximum divert, and thrust-pointing or velocity constraints [31, 36]. Documented extensions include general nonconvex input sets, affine or quadratic state constraints, some mixed-integer or binary inputs, fixed time of flight, and conservative conic obstacles [25]. A representative lander model assumes thrust and gravity dominate, aerodynamics are negligible, gravity is constant under a flat-planet model, and high-bandwidth attitude control decouples translation and rotation [51]. A 3-DoF trajectory cannot impose general attitude constraints and needs 6-DoF validation [25]; obstacle avoidance generally needs successive convexification rather than LCvx alone [51]. Thus LCvx informs drone guidance when its reduced model and control geometry fit, but the direct drone evidence below concerns a 3-DoF translational trajectory tracked by closed-loop control [44].

| Documented case | LCvx attribution and result | Evidence status |
|---|---|---|
| **G-FOLD/Masten Xombie, 2012–2013**; the review describes a **3-year, 7-flight** campaign | JPL, Masten Space Systems, and university partners; convexified powered-descent guidance on a sounding rocket; **100 ms** on a **1.4-GHz Intel Pentium M**; Bsocp was also run on a radiation-hardened BAE RAD750 [21, 31]. | Onboard flight-test evidence of real-time feasibility, not operational commercial deployment. |
| **ACL custom quadrotors, IROS 2017** | LCvx enabled an agile flip; LCvx plus SCvx handled an obstacle-space case. Minimum mean times were **36.5 ms** on mobile ARM and **122.2 ms** on Intel processors [44]. | Flight demonstration; hardware, horizon, discretization, solver, and tolerance are not fully matched. |
| **Rotating-space-station docking, 2019 publication** | Multiple-input LCvx numerical example: **K = 4 of M = 12** acceleration vectors and **135 s** time of flight [45]. | Numerical example, not flight; the runtime comparison is the stated desktop result. |

LCvx is an exact-reformulation method: for a large class of non-convex control constraints, it converts them into an equivalent convex problem, preserving feasibility and optimality under the class assumptions [34]. Açıkmeşe and Blackmore’s paper was published on 21 February 2011 [63]. It suits structured powered-flight/landing problems; broader nonlinear cases may need sequential convexification [34][43].

LCvx addresses autonomous-vehicle trajectory generation by changing selected nonconvex optimal-control formulations into convex relaxations that can retain global optimality under stated conditions; its documented scope includes autonomous spacecraft and planetary soft landing, as well as spacecraft rendezvous path planning [38] [39] [64].

LCvx supplies the survey’s distinct lossless-convexification case: slack-variable relaxation and variable reformulation turn selected nonconvex powered-descent and control-constrained problems into convex SOCPs, with conditional global-optimality guarantees and documented Mars powered-descent applications [54] [38] [59] [64].

LCvx connects reliability to conditional global optimality: for the stated continuous-time nonlinear-dynamics and nonconvex-control class, the relaxed optimum is globally optimal for the original problem, while the convex reformulation is computationally simpler  [64]. In reported studies, problems that could take hours with MICP were solved in seconds, while a case with 55 time-discretization points reported 14.3 s and 14.74 s; these are implementation-specific indicators rather than a universal onboard-latency guarantee [39] [59].

Here, “mainstream” means established or popular within the defined convex-trajectory-optimization boundary rather than an exhaustive census or universal adoption: LCvx is described as an established or watershed method, while SCvx and GuSTO are identified as popular SCP algorithms, which justifies this fixed roster [25] . For autonomous-vehicle trajectory generation, reliability means conditional preservation of feasibility and optimality, whereas efficiency means replacing a difficult mixed-integer formulation with a tractable convex or SOCP solve; this remains a qualified claim for selected LCvx problems [38] [39] .

LCvx introduces slack variables for lower-bounded control geometry, uses variable substitutions to remove powered-descent nonlinearities, and discretizes the result into a convex SOCP; exactness holds only under the stated model conditions [38] [59] [60]. The supported nonconvexity sources are nonlinear or mass-varying dynamics and thrust/control norms, including semi-continuous inputs; the baseline class keeps state constraints convex and provides no basis here for attributing nonconvexity to obstacles, free final time, or mission objectives [38] [39] [60].

Across the named roster, only LCvx is quantitatively documented here: its exactness, global-optimality, and polynomial-time SOCP claims are conditional, and a case with 55 time-discretization points reports 14.3 s and 14.74 s; no comparable SCvx or GuSTO runtime, memory, hardware, warm-start, feasibility-handling, horizon, tolerance, or application provenance is supplied, so no cross-method or onboard ranking is justified [38]  [59]. For autonomous vehicles, LCvx changes selected powered-descent and path-planning formulations into convex problems for planetary spacecraft, landers, and UAVs, with the supported cases tied to those model assumptions rather than to an unverified deployment claim [51] [52].

LCvx supports the motivation because its convex relaxation can retain global optimality; reported 55-point rocket-landing runs took 14.3 s and 14.74 s, so these formulation-specific results do not establish universal onboard efficiency [32] [59] [61].

LCvx exemplifies convex optimization’s trajectory-generation advantage by replacing selected nonconvex constraints with a convex SOCP whose solution can be globally optimal; under limited onboard resources, a case with 55 time-discretization points took 14.3 s and 14.74 s, so these figures indicate tractability but not a universal latency or memory guarantee [38]  [59]. LCvx is treated independently as suitable for planetary soft landing and UAV path planning when its convexifiable model assumptions hold, with reported initial-state and model limits constraining transfer [51] [52] [61].

## SCvx: Successive Convexification

### Core idea and working principle

**SCvx repeatedly improves a local model.** Successive Convexification, abbreviated SCvx, solves a nonconvex optimal-control problem by constructing and solving a sequence of convex approximations. At each iteration, nonlinear dynamics and appropriate nonconvex constraints are approximated around a reference trajectory.

**Its scope developed beyond nonlinear dynamics.** The 2016 analysis assumes that state and control constraints are already convex or convexified, concentrating on nonlinear dynamics. Subsequent formulations cover broader nonconvex state and control restrictions, six-degree-of-freedom motion, aerodynamic forces, free final time, and conditionally enforced constraints. SCvx is therefore best understood as a family of related algorithms whose particular safeguards and guarantees depend on the formulation. [7]

**Linearization creates the convex dynamics model.** For a reference pair \((\bar x,\bar u)\), a first-order local approximation at a fixed time can be written schematically as:

\[
\dot x\approx f(\bar x,\bar u,t)+A(t)(x-\bar x)+B(t)(u-\bar u).
\]

The matrices \(A\) and \(B\) are derivatives of the nonlinear dynamics with respect to state and control. This expression is affine in the new optimization variables.

**A local model creates two hazards.** First, its dynamics can make the current subproblem infeasible even when the original nonlinear problem is feasible. Second, allowing large changes can produce an inaccurate or artificially unbounded approximation.

**Virtual control repairs artificial infeasibility.** An auxiliary input is added to the linearized dynamics:

\[
\dot x=f(\bar x,\bar u,t)+A(t)(x-\bar x)+B(t)(u-\bar u)+E(t)\nu(t).
\]

The synthetic input \(\nu\) allows the local model to bridge a dynamics mismatch that would otherwise prevent progress. For a vehicle, it can be interpreted as a fictitious acceleration or dynamic correction.

**A strong penalty discourages fictitious actuation.** The objective includes a large penalty on virtual-control use. In successful convergence, the artificial input disappears to the selected numerical tolerance, leaving a trajectory compatible with the physical dynamics. If substantial virtual control remains, the low-cost solution of the convex subproblem does not represent an executable trajectory of the original vehicle. [7]

**Trust regions limit unjustified changes.** A trust region keeps an iterate near the trajectory about which the model was linearized. The original 2016 method uses an explicitly enforced region and compares actual improvement in a nonlinear merit function with the improvement predicted by the convex model.

**Engineering variants use different safeguards.** The 2020 powered-descent implementation instead penalizes changes through a soft quadratic trust region. This avoids explicit rejected-step handling and the need to calculate the actual-versus-predicted reduction ratio. Its authors observed faster convergence for their powered-descent cases, but explicitly did not present a convergence proof for that particular implementation. [7]

**The iteration is a complete optimization.** SCvx generally solves each convex subproblem to optimality, rather than merely taking one local descent step. That increases the work performed within an outer iteration but can reduce the number of outer iterations.

A representative SCvx sequence is:

1. Initialize a state trajectory, input trajectory, and any time variables.
2. Linearize the nonlinear dynamics and relevant nonconvex constraints.
3. Discretize the local dynamics and introduce virtual control and trust-region terms.
4. Solve the convex trajectory subproblem.
5. Update or accept the reference according to the selected safeguard strategy.
6. Stop when trajectory changes and feasibility-related residuals satisfy the prescribed tolerances.

**Free final time fits naturally.** The powered-descent formulation maps the burn interval to normalized time \(\tau\in[0,1]\), with burn duration \(s\) becoming a decision variable:

\[
\frac{dx}{d\tau}=s\,f(x(\tau),u(\tau)).
\]

The physical end time is now optimized without changing the numerical interval. The product involving \(s\) remains nonlinear, but it can be included in the successive local approximation. This makes SCvx attractive when duration and trajectory shape must be chosen together. [7]

**Discretization can preserve useful structure.** The 2020 implementation uses first-order-hold controls: adjacent control values are connected linearly in time. For convex control constraints, interpolation between feasible endpoints remains feasible. The propagation of local dynamics is performed over separate intervals, a multiple-shooting-style structure that also permits interval calculations to be parallelized. [7]

### Advantages and suitable problems

**SCvx handles broader model nonlinearity.** Unlike a single exact LCvx reformulation, SCvx can accommodate nonlinear gravity, aerodynamic forces, and coupled rigid-body dynamics through repeated approximation. The important advantage is model expressiveness: the optimizer can consider effects that materially shape a vehicle’s feasible motion instead of relying on a simplified translation-only representation. [7]

**Six-degree-of-freedom landing is a strong fit.** A six-degree-of-freedom vehicle model includes both translation and rotation. Attitude influences the inertial thrust direction, while gimbaled thrust also produces torque. These couplings are important when a rocket must shed horizontal momentum while respecting tilt, angular-rate, and engine-gimbal limits and arriving upright. SCvx provides a tractable way to optimize this coupled motion. [7]

**Ignition timing adds meaningful freedom.** The 2020 formulation optimizes an engine-off coast interval before powered descent. Choosing when to ignite changes the position and velocity from which the burn begins and can reduce fuel consumption. This is a different capability from merely selecting a fixed-duration landing trajectory: the optimizer chooses both a starting point on the coast trajectory and the subsequent powered maneuver. [7]

**Aerodynamics can shape the maneuver.** The same paper introduces a tractable aerodynamic model capable of representing both drag and lift. Its simulations show the vehicle exploiting lift to bend its trajectory while adjusting attitude and thrust direction. This illustrates why retaining nonlinearity can improve the physical usefulness of the result: aerodynamics need not be treated solely as an external disturbance. [7]

**Conditional constraints broaden mission modeling.** A state-triggered constraint, or STC, expresses a rule such as “if speed exceeds a threshold, restrict angle of attack.” Unlike a constraint imposed over a fixed time interval, its activation depends on the optimized trajectory. This is valuable when a vehicle can choose whether to slow down, change orientation, or otherwise avoid entering a constrained regime. [7]

**Continuous variables can encode the implication.** For an inequality version, let \(g(z)<0\) be the trigger and \(c(z)\leq0\) the required condition. The cited STC construction can be represented as:

\[
-\min(g(z),0)\,c(z)\leq0.
\]

When the trigger holds, the multiplier is positive and the constraint condition is enforced; otherwise, the expression becomes zero. This avoids explicit integer decision variables for that implication, but the resulting relation is still nonconvex and must be handled by the iterative optimizer. [7]

**Drones benefit from the same flexibility.** Obstacle avoidance, constrained passage through a hoop, and cooperative transport can combine nonlinear dynamics with geometric or conditional restrictions. SCvx can incorporate these features without requiring every nonconvexity to satisfy a lossless-relaxation theorem. Its suitability therefore extends from rocket guidance to aerial-robot motion planning. [14]

### Trade-offs and boundary conditions

**Convergence is not universal global optimality.** A convex subproblem has a global optimum, but the sequence of local models still addresses an originally nonconvex problem. The 2016 theory establishes constrained stationarity of limit points for the penalized formulation, with recovery of original-problem stationarity when the relevant feasibility conditions hold.

**Guarantees belong to specific formulations.** The original continuous-time proof assumes differentiable dynamics, a convex differentiable cost, and state and control restrictions already in the required convex form. Later SCvx work expands capabilities and analyzes additional convergence properties. Nevertheless, changing trust-region rules, penalties, constraint treatments, or stopping criteria can change what is established mathematically. [15]

**The practical solver can stop early.** The 2020 landing implementation terminates when virtual-control use and iterate changes are sufficiently small. Its authors explicitly note that continuing iterations can gradually reduce cost further. Thus, a runtime-conscious stopping rule may prioritize a useful feasible trajectory over full local optimization. This is often a sensible guidance trade-off, but the returned result should be described accordingly. [7]

**Initialization affects the final answer.** A better-looking initial trajectory does not necessarily produce a better solution or faster convergence. In the 2020 landing study, initialization from a three-degree-of-freedom solution did not consistently outperform a simple straight-line guess. Some combinations produced higher fuel consumption or longer solve times because the iterative process reached a different region of the nonconvex problem. [7]

**Virtual control does not repair physics.** It helps bypass infeasibility introduced by linearized dynamics; it cannot create a physically feasible trajectory when thrust, terminal conditions, and hard geometric constraints are genuinely inconsistent. A subproblem can appear numerically manageable while the overall process fails to remove artificial actuation.

**Intermediate iterates need not be executable.** Before convergence, an iterate may satisfy the convexified dynamics but violate the original nonlinear dynamics. It may also rely on virtual control. This matters for receding-horizon operation: an optimizer interrupted by a deadline should not automatically hand its newest iterate to the vehicle merely because the latest convex solve succeeded. [7]

**Temporal nodes do not cover everything.** The 2020 implementation enforces state and nonconvex constraints at a finite set of nodes and explicitly notes that violations can occur between them. Linear interpolation preserves convex control restrictions, but it does not automatically preserve collision clearance, nonlinear state bounds, or other nonconvex constraints along the entire continuous trajectory. This is an implementation boundary distinct from convergence of the outer algorithm. [7]

**Repeated solves consume onboard time.** Each outer iteration requires constructing a model and invoking a convex solver. Trust-region contraction, complicated constraints, or a poor reference can increase this burden. A 2022 quadrotor corridor-planning paper specifically identifies slow computation and careful parameter tuning as practical difficulties for a smooth nonconvex corridor formulation solved using SCvx. [16]

### Applications and demonstrated results

**SCvx has both rocket and drone examples.** The rocket literature establishes increasingly expressive guidance formulations, while the quadrotor literature supplies physical flight demonstrations. These two strands should be kept separate: a simulated six-degree-of-freedom lander and a flight-tested three-degree-of-freedom drone planner answer different validation questions.

| Algorithm | Project or study | Vehicle or robot | Application | Evidence level |
|---|---|---|---|---|
| SCvx | Mars landing studies, 2017–2018 | Six-degree-of-freedom Mars rocket model | Powered landing; free final time | Computational studies |
| SCvx | Generalized landing, 2020 | Six-degree-of-freedom rigid rocket model | Aerodynamics, ignition time, STCs | Simulation |
| SCvx | ACL maneuvering, 2017 | Custom quadrotors | Keep-out-zone avoidance | Onboard flight demonstration |
| SCvx | Compound STCs, 2019 | Single quadrotor | Passage through a hoop | Monte Carlo simulation |
| SCvx | Compound STCs, 2019 | Two quadrotors and beam payload | Cooperative obstacle-course transport | Monte Carlo simulation |
| SCvx | Hu et al., 2021 | Small guided rocket model | Three-dimensional ascent | Simulation |
| SCvx | Mceowen et al., 2022 | Autonomous aerial drones | Interactive constrained planning | Flight experiments |

These examples are documented in the 2018 Mars-landing paper [17], 2020 generalized landing paper [7], ACL flight paper [3], compound-STC paper [14], guided-rocket ascent paper [18], and 2022 drone-planning paper [19].

**Mars landing motivated richer dynamics.** Szmuk and colleagues’ 2017 study addressed Mars six-degree-of-freedom powered descent, followed by Szmuk and Açıkmeşe’s 2018 free-final-time formulation. These are specific lander-guidance applications of SCvx, rather than evidence assigning it to a particular commercial rocket. Their importance is that attitude, translation, and duration are optimized together. [10][17]

**The 2020 study quantifies feature costs.** Szmuk, Reynolds, and Açıkmeşe used a notional nondimensionalized rocket scenario with 20 temporal nodes. Across the reported feature combinations, convergence required four to seven successive iterations. The following subset shows how added capabilities affected the resulting local solution and median solver time. [7]

| Simulated feature set | Outer iterations | Fuel consumed | Median solve time |
|---|---|---|---|
| Baseline | 4 | 3.17% | 164 ms |
| Lift and drag | 4 | 3.55% | 276 ms |
| Lift, drag, and STC | 7 | 3.40% | 504 ms |
| Lift, drag, and free ignition | 5 | 3.13% | 241 ms |
| Lift, drag, STC, and free ignition | 7 | 3.21% | 505 ms |

Fuel percentages and times are the paper’s model-specific results; the timing experiments used a 2.2 GHz Intel Core i7 computer, with batches of ten runs per feature combination. [7]

**A counterintuitive result reveals local behavior.** Adding an STC reduced the computed fuel consumption from 3.55% to 3.40% in the aerodynamic case. For a globally solved minimization problem, adding a constraint cannot improve the optimum by enlarging the feasible set—it does not enlarge it. The authors instead suggest that the additional constraint steered the iteration toward a better local minimum. This is evidence of the nonconvex outer problem, not evidence that tighter constraints generally save fuel. [7]

**The timing result is subsecond simulation.** The largest tabulated aggregate solve time is \(0.682\ \mathrm{s}\), consistent with the paper’s statement of a maximum below \(0.7\ \mathrm{s}\). The C++ propagation step was reported separately, with maximum time per run on the order of \(10\ \mathrm{ms}\). The paper treats trajectory generation as a feedforward problem and does not analyze closed-loop recomputation, so these results establish computational promise for that formulation rather than a complete flight-guidance timing guarantee. [7]

**Quadrotor flights establish physical trackability.** The 2017 ACL work applied lossless and successive convexification together to obstacle-avoidance trajectories computed onboard. Across its example scenarios and tested processors, the reported minimum mean computation times were \(36.5\ \mathrm{ms}\) on mobile ARM processors and \(122.2\ \mathrm{ms}\) on Intel processors. These are shared demonstration results, not isolated measurements that rank LCvx against SCvx. [3]

**Compound STCs enable coordinated geometry.** The 2019 IROS study considered a quadrotor passing through a hoop and two quadrotors carrying a beam-like payload through an obstacle course. Compound trigger and constraint conditions use Boolean “and” and “or” combinations within a continuous formulation. Monte Carlo simulations reported trajectory-generation rates upwards of \(3\ \mathrm{Hz}\) for the hoop case and \(1.5\ \mathrm{Hz}\) for paired payload transport. [14]

**Small-rocket ascent shows another problem class.** Hu and colleagues’ 2021 study applies SCvx to three-dimensional ascent for a small guided rocket. It introduces auxiliary controls, virtual controls, and a soft trust region and reports convergence in seven steps from coarse initial guesses. This is a simulation example demonstrating that the framework is useful beyond landing. [18]

**Interactive drone planning reached flight experiments.** Mceowen and colleagues’ 2022 visual modeling system lets users specify trajectory objectives and constraints graphically. A high-level parser constructs an optimal-control problem, SCvx generates convex subproblems, and a lower-level parser converts them into standard SOCP form for an in-house primal-dual interior-point solver. The paper reports illustrative aerial-drone flight experiments, including the ability to update mission specifications during flight. [19]

**SCvx is preferable when modeling dominates.** It is a strong choice for nonlinear, free-final-time, or conditionally constrained guidance when the additional model fidelity justifies repeated convex solves; its advantage weakens when tuning, initialization, or deadline pressure prevents reliable convergence to an executable trajectory.

**Additional documented evidence**

SCvx, or **Successive Convexification**, is an iterative family of algorithms for nonconvex, constrained optimal-control problems. It repeatedly replaces the current nonlinear trajectory problem with a finite-dimensional convex subproblem, rather than relying on one direct convex reformulation. SCvx is therefore aimed at broader combinations of nonlinear dynamics and nonconvex state or control constraints; “successive convex programming” is a wider family label and should not automatically be treated as the specific SCvx method.[36]

**Working principle**

At iteration \(k\), SCvx forms a reference trajectory from the previous iterate, linearizes the nonlinear dynamics and other nonconvex constraints around that reference, discretizes the horizon, and solves the resulting convex problem. The new state and control trajectory becomes the reference for the next iteration, and the loop continues until the changes and feasibility-restoration terms are sufficiently small.[33][34] In common formulations, the subproblem contains incremental state and control variables, convex state and control sets, a penalized objective, and either a trust-region constraint or another mechanism restricting the validity of the local model.[34]

The convex subproblem is often a second-order cone program (SOCP). In the Mars powered-descent formulation, a free-final-time nonconvex problem is transformed into a fixed-final-time SOCP, with first-order linearization about the current state, control, and time-dilation reference. The trajectory is then discretized at \(K\) evenly distributed normalized-time points; the reported implementation also requires nondimensionalized variables and numerically well-scaled initial conditions.[33][74] The nonconvexity in this class of problem includes nonlinear rigid-body dynamics, a nonzero lower thrust bound, thrust-direction restrictions, state constraints, and free final time.[74]

SCvx implementations differ in how they preserve feasibility. The powered-descent formulation uses soft trust regions to prevent an unbounded local model and introduces virtual control to mitigate artificial infeasibility when the linearized dynamics cannot initially be satisfied. The virtual-control term is penalized, so a converged solution with negligible virtual-control cost indicates dynamic consistency.[33] A state-constraint formulation instead uses an exact penalty for the nonlinear dynamics and a **project-and-linearize** procedure: the current point is projected onto each constraint, each constraint is linearized at its own projection point, and the resulting half-spaces define a convex feasible region. That formulation does not require the trust-region update used by the powered-descent formulation; these are distinct SCvx variants rather than contradictory descriptions.[36]

Initialization is consequently formulation-dependent. The general convergence analysis for the project-and-linearize method assumes an initial point \(z^{(0)}\) in the feasible set and a penalty weight, whereas the Mars implementation starts from a simple dynamically inconsistent reference trajectory and uses virtual control to proceed.[33][36] An enhanced SCvx-fast initialization procedure can linearize violated constraints and project an infeasible starting point to a feasible trajectory in **one step**, subject to its stated convexity assumptions.[34]

**Guarantees, advantages, and limitations**

SCvx does not provide unconditional global optimality for the original nonconvex problem. Under the project-and-linearize formulation’s assumptions—including convex compact state and control sets, suitable differentiability and convexity of the dynamics and state constraints, LICQ, Slater’s condition, and a nondegenerate feasible region—the successive sequence has a limit point that is a local optimum of the penalized problem. Exact-penalty reasoning recovers local optimality for the original problem when the penalty weight is sufficiently large and the limiting point is feasible.[36] More general SCvx analyses establish stationarity, KKT conditions when the limit point is feasible, and superlinear convergence under additional regularity, Lipschitz-gradient, Kurdyka–Łojasiewicz, or related assumptions. Convergence alone does **not** guarantee feasibility of the original nonconvex problem.[34]

For the 6-DoF Mars landing formulation, proper initialization and feasibility of the original problem are required before the stated guarantee applies: the converged solution then satisfies the original dynamics, kinematics, and constraints. Termination occurs when both the trust-region change and the virtual-control norm fall below their prescribed tolerances.[33] In the reported notional simulations, the 2-D case converged by the **sixth iteration** and the 3-D case after **nine iterations**; these are observations for those simulations, not iteration guarantees for arbitrary missions.[33] The same study used **50 time-discretization points** and imposed a maximum of **15 iterations**.[33]

The principal computational advantage is that every local problem is convex and can be solved to the accuracy of the selected SOCP solver. First-order Jacobians avoid Hessian construction, while trust-region updates regulate linearization error. For simple convex sets such as second-order cones, the subproblem can be solved in milliseconds in suitable implementations; interior-point methods also provide deterministic stopping criteria.[34][74] A reported comparison using ECOS on a workstation with an Intel Xeon processor at **3.40 GHz** and **16 GB of RAM** measured **14 iterations and 149.9 ms** for SCvx, versus **7 total iterations and 65.7 ms** for SCvx-fast.[34] These figures are benchmark observations, not portable onboard performance measurements: horizon length, discretization, tolerances, solver settings, and hardware must be matched before comparing runtimes.

The trade-off is broader modeling reach at the cost of repeated solves, local approximation, and weaker guarantees than a genuinely exact convex reformulation. Performance depends on discretization accuracy, the region of attraction of the initial guess, the quality of local linearizations, penalty weights, and trust-region updates.[33][34] Poor initialization or an unrealistically short time-of-flight can create artificial infeasibility; extrapolating a local linear model too far can create artificial unboundedness. Trust regions contract after rejected or inaccurate steps and are retained or enlarged only when the predicted and actual improvements agree sufficiently.[34] SCvx generally returns a local solution, and highly cluttered environments with many obstacles can still make it difficult to find a good local optimizer.[34] Collision-avoidance formulations may also require obstacles to be convex or convexly decomposable; occupancy-grid obstacles often do not satisfy that assumption. A reported full-quadrotor multi-drone problem with smooth robust signal-temporal-logic semantics was not solved efficiently in real time, illustrating that the convexification framework does not remove all scaling and representation difficulties.[34]

**Relevance and documented applications**

SCvx directly addresses the survey’s autonomous-vehicle focus because it handles trajectory generation with nonlinear dynamics, actuator restrictions, collision avoidance, and mission constraints rather than only geometric path planning. Documented contexts available by the requested cutoff include:

- **Mars powered descent:** the 6-DoF rocket-powered landing study solves a minimum-time trajectory with mass, position, velocity, attitude, angular-rate, thrust-magnitude, pointing, tilt, and glide-slope constraints. Its evidence is a notional 2-D/3-D numerical simulation, not a reported flight, operational mission, or confirmed onboard deployment; the cited record does not identify a company’s rocket.[33]
- **Quadrotor or multi-rotor obstacle avoidance:** the SCvx study models a multi-rotor with double-integrator dynamics, speed and acceleration bounds, a thrust-cone constraint, nonlinear aerodynamic drag, and cylindrical keep-out zones. The documented evidence is numerical simulation; no physical deployment is established in the cited span.[36]
- **Powered-landing literature:** a **2016** conference record attributes Successive Convexification to fuel-optimal powered landing with aerodynamic drag and nonconvex constraints, while a **2017** record attributes it to Mars 6-DoF powered-descent landing guidance. These records establish method-to-scenario mappings, but leave organization, specific vehicle, event date, and deployment status unspecified.[36]
- **Road-vehicle planning:** an SCvx-STL adaptation investigates autonomous-vehicle motion planning with signal-temporal-logic constraints and demonstrates capabilities and drawbacks on CommonRoad road-motion-planning benchmarks. This is a benchmark or thesis study, not evidence of operational deployment.[65]

A separate implementation reports aggressive quadrotor guidance trajectories generated onboard at rates exceeding **8 Hz** using a customized in-house interior-point solver, and refers to autonomous rocket-landing experiments; the cited evidence does not supply enough hardware, problem-size, company, or flight-status detail to generalize that rate or identify a particular rocket.[34] Conversely, a cited quadrotor-fleet paper is described only as **sequential convex programming**, so it should not be counted as a verified SCvx application without direct method attribution.[36]

SCvx (Successive Convexification) linearizes nonlinear dynamics and nonconvex state/control constraints about a reference, then solves successive convex subproblems and reuses each solution as the next reference. Virtual control, penalties and trust regions mitigate artificial infeasibility and unbounded steps. [75][71]

Applications include simulated 6-DoF powered descent with state-triggered angle-of-attack and collision-avoidance constraints and nonconvex quadrotor planning [71][77]. SCvx-fast targets simpler dynamics and convex keep-out zones; its project-and-convexify variant reportedly enables more aggressive, fewer-iteration steps. [76]


SCvx iterates SOCPs; guarantees are conditional [43]. Cases: Apollo CSM–LM docking (2019 paper/offline) ; Mars 6-DoF landing (2018 paper/simulation) [43]; ACL quadrotor flight (2017/demo) [44].

SCvx suits nonlinear powered-descent/landing with drag, thrust/state/path and state-triggered constraints, including 6-DoF PDG, but initialization, discretization, scaling and trust-region tuning affect reliability [32]. A 2018 paper reports minimum-time 6-DoF Mars rocket-landing SCvx in 2-D and 3-D simulations; Mars, reusable launch vehicles (including SpaceX boosters), lunar exploration and asteroid sample return were potential—not deployed—applications [80]. It reports 10–15 iterations (2018), but no comparable solve-time or flight record [80].

Each subproblem is globally solvable, not the original nonconvex problem itself. Under differentiability, convexity, penalty, regularity and feasibility assumptions, SCvx has global/superlinear convergence results; local optimality requires original feasibility and zero virtual terms [48]. Linearization can cause artificial infeasibility/unboundedness; safeguards mitigate, but initialization, discretization and model fidelity still matter [48].

It suits nonlinear vehicle dynamics, state/control limits and obstacle avoidance: cases include autonomous-vehicle planning with cylindrical/ellipsoidal obstacles, drone/quad-rotor planning and rocket landing [70][48][83]. A quad-rotor example used 16 iterations versus about 36 for SQP; onboard implementation exceeded 8 Hz, though runtime was not compared [48]. Generic SCP—not SCvx—reported 40 iterations and 24–52 s on an Intel i5/8-GB laptop; do not transfer those figures [81].

Evidence is simulation or demonstration: obstacle planning was simulated [70]; Mars 6-DoF landing was a reported study [83]; SCvx-fast, a labeled variant, used 11 SOCPs in a multi-rotor numerical test [82]. The quad-rotor case is explicitly a flight demonstration on an onboard embedded processor, but no company, date, geography or operational deployment is established [48].

SCvx (Successive Convexification) repeatedly linearizes nonlinear dynamics and non-convex path/state/control constraints, then solves convex subproblems for time-critical landing and obstacle-avoiding planning [69]. Cases include a 6-DoF Mars rocket landing and linked quadcopter trajectories through obstacles [33][69].

SCvx (Successive Convexification) is the survey’s sequential-convex-programming case: it converts nonconvex trajectory optimization into temporary discretized convex problems and supports fully autonomous onboard planning [68][73][76]. Applications include Mars landing and SCvx-VSCMO manipulation on a 4 DOF planar arm and a 7 DOF Sawyer from Rethink Robotics, with hardware execution for Sawyer [33].

SCvx supports the reliability–efficiency premise conditionally: convex subproblems are reported as quickly solvable for real-time use, and SCvx/SCvx-fast as an onboard-planning pillar [76]. Linearization and repeated solves still cost computation; robustness depends on virtual-control/buffer safeguards and problem complexity [34].

For SCvx, reliability means safeguarded local convergence/feasibility, and efficiency means tractable convex inner solves for onboard use—not global optimality of the original problem; a formulation reports 11 SOCPs [34][44][82]. Linearization, initialization, virtual control, trust regions and penalties add conditionality and work [34][37].

“Mainstream” is operationally the fixed user-specified roster, not an exhaustive prevalence ranking; SCvx is explicitly retained and classified within sequential convex programming [68][73].

SCvx starts from a reference, linearizes and discretizes nonlinear dynamics/constraints, solves a convex SOCP with incremental variables, convex sets, a penalized objective and a trust region, updates the reference, and stops on convergence or an iteration limit [34][73]. Trust regions bound inaccurate steps and virtual control mitigates artificial infeasibility; repeated solves are efficient but leave local, discretization- and initialization-dependent behavior [37][34].

For SCvx, nonconvexity comes from nonlinear dynamics and state/control or path constraints, with cases involving obstacle avoidance, thrust/control constraints and free-final-time decisions; a penalized objective represents trajectory cost [36][44][72][34]. Successive local linearization handles these cases, so the reformulation is not a universal exact convex model [71][68].

The available quantitative SCvx evidence is not a cross-method benchmark: it reports 11 SOCPs for a formulation [82], but supplies no matched hardware, runtime, memory, iteration denominator or reliability measure for LCvx, SCvx and GuSTO together. No ranking should be inferred.

SCvx directly serves autonomous-vehicle research by repeatedly convexifying nonlinear optimal-control/path-planning problems, including rocket landing, quadrotor obstacle avoidance and autonomous parking with state-triggered constraints [33][44][66]. Its survey contribution is the general sequential case; real-time inner solves support efficiency, but reliability remains conditional on local approximation and safeguards [73][79].

Each SCvx iteration linearizes and discretizes a current trajectory, solves an SOCP with trust-region and virtual-control safeguards, updates the reference and stops on convergence criteria; it suits fixed/free-final-time, linked-trajectory and collision-avoidance problems [67][79][73][69]. Under convex/convexified constraints and the stated regularity conditions, limit points are stationary and exactness can recover original-problem stationarity; otherwise results are local and initialization-dependent [34].

SCvx (Successive Convexification) is a central pillar for onboard planning in a fully autonomous system [76]. Its distinct survey value is showing the sequential route from a nonconvex problem to repeated convex subproblems, with 11 SOCPs reported in a documented formulation [34][82].

That structure supports onboard use but not an unconditional guarantee: each local subproblem uses incremental state/control variables, convex sets, a penalized objective and a trust region, while solution quality is locally optimal and initialization-dependent [34]. SCvx is appropriate for nonlinear trajectory optimization when the convexified model and safeguards are valid.

SCvx shows the onboard value of convex optimization: fast convex inner solves and feasibility safeguards support real-time planning, with SCvx positioned as a central onboard-planning pillar [76]. A reported LCvx/SCvx asteroid-reference case took 35 [s], but no matched memory, latency or warm-start baseline is supplied [73].

SCvx handles nonlinear dynamics and constraints through successive convexification, using trust regions and virtual control or relaxation against artificial infeasibility/unboundedness; it suits nonlinear optimal control and convex keep-out-zone collision avoidance [79][78]. Its limits are local-model accuracy, initialization/region dependence and conditional convergence/feasibility [34].

## GuSTO: Guaranteed Sequential Trajectory Optimization

### Core idea and working principle

**GuSTO emphasizes continuous-time optimal-control structure.** Bonalli, Cauligi, Bylard, and Pavone introduced Guaranteed Sequential Trajectory Optimization in 2019. It is a sequential convex programming framework for nonlinear systems that are affine in control and may have drift.

**Control-affine does not mean linear dynamics.** GuSTO considers systems of the form:

\[
\dot x(t)=f_0(x(t))+\sum_{i=1}^{m}u^i(t)f_i(x(t)).
\]

The inputs \(u^i\) enter linearly, but their influence can depend nonlinearly on the state through the vector fields \(f_i(x)\). The drift term \(f_0(x)\) describes motion that occurs even without control.

**Goal sets permit useful terminal freedom.** Rather than requiring one exact terminal vector, the formulation allows \(x(t_f)\in M_f\). This can represent a family of acceptable end configurations. That flexibility is useful in robot planning because overprescribing terminal coordinates may exclude lower-cost or more easily reachable solutions.

**Local approximation generates successive subproblems.** GuSTO linearizes nonlinear contributions around the previous trajectory and control. The dynamical approximation becomes affine in the new state and input variables, while suitable convex cost components can be retained. The paper calls the resulting iteration a linearized optimal-control problem.

**Dynamics and state constraints receive different treatment.** The local dynamical equations and endpoint requirements are imposed as constraints, while state-constraint violations—such as penetration into an obstacle—are penalized in the objective. A weight \(\omega_k\) controls the strength of that penalty.

**Hard dynamics refers to the current model.** At an intermediate iteration, the enforced dynamical equation is the local linearized equation. Its agreement with the original nonlinear equation is part of the convergence analysis and model-accuracy assessment. Thus, hard enforcement of the subproblem dynamics should not be interpreted as original nonlinear feasibility of every intermediate trajectory.

**A state trust region controls approximation.** GuSTO penalizes excessive changes in the state trajectory relative to the previous iterate and adjusts the trust-region size as computation proceeds. Its original construction concentrates this restriction on the state because controls enter the dynamics affinely.

**Model accuracy governs step acceptance.** After solving a candidate subproblem, the algorithm checks whether the intended trust-region condition is satisfied. It then evaluates a relative-error measure involving differences between the original and approximated costs and dynamics.

**Penalties drive state-constraint satisfaction.** If a candidate does not satisfy the required state constraints to the chosen tolerance \(\varepsilon\), the state-constraint weight is increased. If the candidate satisfies only the soft trust-region condition, the weight can also be increased while the trust-region size is held fixed.

A concise version of the iteration is:

1. Choose an initial state/control curve, final-time guess, trust-region size, and penalty weight.
2. Construct and solve the locally approximated trajectory problem.
3. Check the intended trust region and assess original-versus-local model error.
4. Reject inaccurate candidates and shrink the region, or accept candidates and update it.
5. Increase penalties when state constraints or the intended trust region remain unsatisfied.
6. Terminate on sufficiently small iterate changes, or return failure if the penalty exceeds its specified maximum.

**The implementation leaves discretization choices open.** GuSTO’s theory is formulated in continuous time, rather than being tied to one temporal grid. The original numerical experiments use trapezoidal discretization with zero-order-hold control and approximately 30–40 discretization points.

### Advantages and suitable problems

**Robot planning is GuSTO’s natural setting.** Its examples combine nonlinear dynamics, collision avoidance, control bounds, and terminal freedom. These are common requirements for free-flying spacecraft robots and aerial vehicles in cluttered environments.

**Infeasible initialization can still be useful.** GuSTO does not require the initial curve to be dynamically feasible or collision-free. A straight line through state space can serve as a starting reference, while the penalty and trust-region mechanisms attempt to refine it.

**Penalized collision constraints allow recovery freedom.** If an initial curve passes through an obstacle, imposing all local collision restrictions as hard inequalities can make a subproblem difficult or inconsistent. Allowing temporary state-constraint violation gives the optimizer room to move the trajectory before demanding final clearance.

**The guarantee uses Pontryagin stationarity.** Under its assumptions, GuSTO establishes convergence properties leading to a Pontryagin extremal: a state/control trajectory accompanied by nontrivial adjoint variables satisfying necessary optimality conditions. This is more informative than saying that the objective stopped changing.

**The theorem describes precise convergence modes.** For an infinite sequence, the paper establishes a convergent subsequence under the specified topologies: final times converge, state trajectories converge uniformly, and controls converge weakly in an appropriate function space. It also establishes convergence of the associated Pontryagin multipliers.

**Dual information creates an acceleration opportunity.** Multipliers from the sequential trajectory problems approximate the costates used by indirect optimal-control methods. GuSTO can use this information to initialize a shooting method, which solves the optimality boundary-value equations.

### Trade-offs and boundary conditions

**The assumptions are substantive.** GuSTO’s “guaranteed” label refers to a theorem with explicit regularity, compactness, and feasibility conditions.

| Assumption | Main mathematical condition | Practical meaning |
|---|---|---|
| A1 | Compact convex controls; compact goal submanifold | Actuator and terminal sets need compatible structure |
| A2 | Smooth model terms with compact support | Model regularity must hold over the working domain |
| A3 | Feasible local problems; bounded free final time | Every iteration must admit a solution |
| A4 | Continuous optimal controls for local problems | The convergence argument uses control regularity |

**Local feasibility is especially important.** The analysis assumes each linearized optimal-control problem is feasible. The paper discusses virtual-control constructions as one way to help satisfy that condition. Consequently, “GuSTO enforces dynamics hard” should not be turned into a categorical claim that auxiliary feasibility mechanisms can never appear in a GuSTO-based implementation.

**Stationarity is weaker than optimality.** A Pontryagin extremal satisfies necessary conditions; it need not be a global minimum and is not automatically a local minimum without additional conditions. GuSTO’s guarantee is therefore different from an eligible LCvx exact-relaxation result.

**State constraints have a numerical tolerance.** The algorithm seeks state-constraint satisfaction up to a selected \(\varepsilon\). For collision avoidance, that tolerance must be interpreted relative to obstacle geometry, model units, and the trajectory’s numerical representation.

**Failure remains a defined outcome.** GuSTO terminates unsuccessfully if the state-constraint penalty exceeds a specified maximum without achieving the required satisfaction. The paper explicitly associates this with an infeasible problem or an initialization that the algorithm could not refine to feasibility.

**Model complexity can defeat simple initialization.** In the paper’s eight-dimensional airplane example, a straight line in the full state space caused failure for all three compared sequential methods. A dynamically feasible initialization, and especially a dynamically feasible collision-free initialization, changed the result.

**Continuous-time analysis does not excuse coarse grids.** The theoretical guarantee is not tied to one discretization scheme, but a numerical implementation must still approximate the continuous problem adequately. The paper itself relates the continuous-time conclusion to sufficiently small time steps.

### Applications and demonstrated results

**GuSTO includes an identified hardware platform.** The original paper’s hardware experiment used a free-flying robot at the Stanford Space Robotics Facility. It was a fully holonomic, three-degree-of-freedom system with eight thrusters and a reaction wheel, maneuvering on a frictionless surface. The task was to navigate clutter and berth with a capturing spacecraft.

| Algorithm | Project or study | Organization and vehicle | Application | Evidence level |
|---|---|---|---|---|
| GuSTO | Free-flyer comparison, 2019 | Stanford; 12-state Astrobee-like model | Cluttered ISS mock-up navigation | 100 simulation trials |
| GuSTO | Airplane initialization study, 2019 | Eight-state airplane model | Goal-set planning through clutter | Simulation |
| GuSTO | Shooting acceleration, 2019 | Dubins car and spacecraft models | Faster trajectory refinement | Simulation |
| GuSTO | Space Robotics Facility experiment, 2019 | Stanford planar free-flyer robot | Cluttered approach and berthing | Ground hardware experiment |
| GuSTO | Companion software examples | Quadrotor and Astrobee models | Robot trajectory generation | Repository simulations |

The dated experiments and numerical studies are described in the 2019 paper ; software scenarios are identified in GuSTO.jl [20] and the quadrotor/Astrobee companion implementation [21].

**The main batch result is 97 successes.** Bonalli and colleagues ran 100 simulations with different start and goal states for a twelve-dimensional free-flying spacecraft model. Its states comprised position, velocity, attitude parameters, and angular velocity. The parameters were modeled after NASA’s Astrobee robot, and the environment was a cluttered mock-up of the International Space Station.

**The comparison supports a bounded conclusion.** TrajOpt also succeeded in 97% of those trials, while GuSTO was faster on average and returned higher-quality solutions in that experiment. The simple initialization used a straight position path and a geodesic attitude path, with no control initialization.

**The SCvx comparison used a specific adaptation.** For Mao and colleagues’ 2016 method, the GuSTO authors imposed linearized collision-avoidance constraints as hard inequalities because that earlier formulation did not directly address those nonconvex state constraints. It had a high failure rate when the simple initialization lay deeply in collision.

**The airplane study exposes initialization effects.** The eight-state model included position, course, speed, flight-path angle, roll angle, and angle of attack.

| Airplane initialization | GuSTO | TrajOpt comparison | Adapted 2016 SCvx comparison |
|---|---|---|---|
| Straight line in eight-state space | Failure | Failure | Failure |
| Dynamically feasible; possibly colliding | Feasible result | Collision | Convergence criterion unmet |
| Dynamically feasible and collision-free | Feasible; 0.55 s | Feasible; 2.67 s | Failure |



**Good initialization improved practical usefulness.** With the highest-quality airplane initialization, GuSTO reduced the initial trajectory’s cost by 55%, compared with 49% for TrajOpt, while the reported runtimes were \(0.55\ \mathrm{s}\) and \(2.67\ \mathrm{s}\), respectively.

**Shooting acceleration reduced refinement time.** In the original paper’s simulations, using sequential convex programming to initialize shooting reduced total time from \(94\) to \(45\ \mathrm{ms}\) for a Dubins car and from \(570\) to \(146\ \mathrm{ms}\) for the free-flyer. The number of sequential iterations fell from 12 to 6 and from 11 to 3, respectively, while the reported cost remained the same within each example.

**Those timings have a specific computational basis.** The numerical experiments ran on a Linux system with a 4.3 GHz processor and 32 GB of RAM. A shooting attempt required less than \(1\ \mathrm{ms}\), making it inexpensive relative to a sequential iteration in those examples.

**The hardware task validates physical execution.** The Stanford ground robot demonstrates that GuSTO-generated motion can support a physical spacecraft-like approach-and-berthing experiment.

**Astrobee simulations and ISS operation differ.** The companion repository explicitly describes quadrotor and Astrobee simulation examples. NASA’s Astrobee robots were also real ISS platforms by the survey cutoff, including documented independent activities by Queen and Bumble on 7 April 2022. The existence of that operational robot does not turn an Astrobee-modeled GuSTO simulation into an on-orbit GuSTO demonstration. [21][22]

**GuSTO is preferable for compatible robot problems.** Its strongest case combines control-affine dynamics, collision and goal-set planning, continuous-time stationarity analysis, and useful initialization or acceleration opportunities; the recommendation changes when its feasibility assumptions or required state-constraint tolerance do not match the application.

**Additional documented evidence**

**GuSTO: identity and role**

GuSTO means **Guaranteed Sequential Trajectory Optimization**. It is a named **Sequential Convex Programming (SCP)** framework for trajectory optimization of control-affine systems with drift, rather than a synonym for every sequential-convex method. The foundational paper was submitted on **1 March 2019** and published at ICRA 2019, whose conference dates were **20–24 May 2019**; it was added to IEEE Xplore on **12 August 2019**, well before the survey cutoff of 2022-12-31. [86] GuSTO therefore supplies the requested method-specific case for autonomous-vehicle trajectory generation: it is designed to produce trajectories for nonlinear robotic systems while accommodating goal-set constraints and either fixed or free final time. [86]

**Working principle**





**Guarantees, advantages, and limitations**


GuSTO’s principal benefits are therefore conditional rather than universal. It offers a systematic way to handle control-affine nonlinear and nonconvex dynamics, drift, nonholonomic systems, state and control constraints, collision avoidance, goal sets, and free final time within one SCP framework. The method also provides a theoretically justified stopping criterion, trust-region adaptation, and an accelerated implementation that incorporates ideas from indirect optimal control.  In numerical experiments on a range of trajectory-optimization setups, the authors report that GuSTO generally outperformed the compared state-of-the-art approaches in **success rates, solution quality, and computation times**. Those results establish comparative evidence for the tested numerical problems, not a hardware-independent guarantee of reliability or efficiency. [86]



**Documented applications and evidence status**

The pre-cutoff GuSTO paper documents the following method-attributed examples:



Accordingly, the documented GuSTO record supports numerical demonstrations, vehicle models, and one laboratory free-flyer experiment. It does not, in the cited evidence, establish a GuSTO flight or mission deployment on a named planetary lander, drone, rocket company’s vehicle, or operational autonomous vehicle. The Mars-landing and quadrotor entries show the relevance of the surrounding toolkit to lander- and drone-like problems, but their exact GuSTO attribution and event dates remain unsupported. The application list is illustrative, and publication dates must not be mistaken for application dates. [86]

Finally, **GuSTO** must be distinguished from unrelated uses of similar capitalization. A 2010 hardware-design paper uses **GUSTO** for “General architecture design Utility and Synthesis Tool for Optimization,” a Matlab tool for matrix-inversion architecture exploration, not trajectory generation. [41][42] A separate NASA balloon observatory also uses the uppercase name **GUSTO**; its documented mission profile scheduled a late-2022 launch, a semiautonomous 0.9-m telescope, and approximately 100 days aloft, but it contains no attribution to the GuSTO trajectory-optimization algorithm. [87] Neither record is a GuSTO application.



Through 2022, GuSTO was tested in Astrobee-like, airplane, and Dubins-car simulations and on a three-DoF/eight-thruster free-flyer hardware test at Stanford; 97% of 100 trials succeeded . Warm-started shooting cut runtime from 94 to 45 ms (car) and 570 to 146 ms (free-flyer) . A 2020 neural warm-start study reduced mean SCP iterations from 4.03 to 3.33 across 1,130 cases [84]. These are study-specific, not deployment evidence.

As of 2022-12-31, GuSTO and TrajOpt each achieved 97% collision-free success in 100 free-flyer simulations. On Linux (4.3 GHz, 32 GB RAM; 30–40 trapezoidal nodes), SCP used 11 iterations/570 ms, versus 3/146 ms with dual-warm-started shooting (74% less time); the 3-D Dubin’s-car case used 12/94 ms versus 6/45 ms (52%) [93]. These are study-specific, not onboard guarantees.

The ECE 602 Winter 2019 Project used MATLAB and 3-D Dubin’s-Car simulation for 2-D obstacle avoidance; it reports relatively few iterations but no organization, flight, mission, or deployment [92]. A 2021 thesis links GuSTO to spacecraft robotic manipulation and an Astrobee gripper, while its hardware results are not proof of onboard GuSTO; grasp waypoints were future work [95][93]. GuSTO.jl’s `freeflyerSE2`/`AstrobeeRobot` examples use JuMP with Gurobi/Ipopt and are notebook evidence only [94]. No company rocket is verified by the cutoff [25][95]; uppercase GUSTO hardware-tool and 2022 balloon-observatory records are unrelated [96][97].

GuSTO addresses autonomous-vehicle trajectory generation by sequentially convexifying nonlinear, constrained control-affine systems with drift to produce locally optimal, dynamically feasible trajectories; Astrobee’s free-flying spacecraft is a documented example [84].

GuSTO is the requested SCP method, “Guaranteed Sequential Trajectory Optimization,” in the LCvx-SCvx-GuSTO roster. It contributes a distinct framework with convergence guarantees, goal-set and fixed/free-final-time support, and numerical evaluation for robotic and aerospace trajectory optimization [68][86][90][89].

GuSTO’s reliability-efficiency evidence is conditional: local convex approximations and off-the-shelf solvers satisfied all constraints in 1130 validation problems, while warm-starting cut iterations by 57% in challenging cases [84][93]. It was reported faster and more accurate than recent SCP solvers, but these are experiment-specific results, not a universal onboard-latency guarantee .

For autonomous-vehicle use, “mainstream” means a named, published SCP trajectory-optimization framework with theoretical and numerical evaluation: GuSTO (2019) qualifies within the requested LCvx-SCvx-GuSTO roster, without implying an exhaustive ranking; its reliability/efficiency claim is conditional because local convex subproblems and trust-region safeguards produced faster, more accurate solutions than recent SCP solvers, not a universal guarantee [88][92]. GuSTO linearizes dynamics and constraints around an initially possibly infeasible trajectory, solves convex subproblems with model-accuracy, trust-region and penalty updates, and under stated assumptions converges to a feasible Pontryagin-stationary solution; it covers drift control-affine systems, collision/goal constraints, fixed/free final time, and tests using 30-40 discretization points [85][91][93].

GuSTO handles nonconvexity from nonlinear/nonholonomic drift dynamics and collision/state constraints by reference linearization and local convex programs; goal sets and fixed/free final time remain supported, so it suits constrained robotic vehicles but remains local and initialization-sensitive [85]. Reported autonomous-vehicle tests used 30-40 discretization points and SCP baselines, but provide no matched hardware, memory, latency, horizon, or tolerance denominators for a cross-method onboard claim .

GuSTO serves autonomous-vehicle research by applying SCP to nonlinear constrained motion planning and producing locally optimal, dynamically feasible trajectories; documented context includes Astrobee and aerospace/robotic systems [84]. As a survey case, it is a generalized control-affine-with-drift framework: each iteration linearizes, solves a convex subproblem, adapts trust regions/penalties and repeats toward a stationary point under stated assumptions, with goal-set and fixed/free-time support; speed/quality gains remain local experimental evidence rather than a universal onboard claim [86][85][91][92].

GuSTO makes each local approximation a convex subproblem and adds trust-region, virtual-control and soft-state mechanisms; its distinct contribution is a theoretically analyzed SCP framework [91][92]. Under limited onboard resources, the optimization workload remains iterative and convex-subproblem based, but GuSTO requires a reference trajectory and no matched memory, latency, or deployment measurements establish onboard performance; it suits drift control-affine systems with control/state, collision and goal constraints and fixed/free final time, while remaining a local method [92][91].

GuSTO (Guaranteed Sequential Trajectory Optimization) is a sequential-convex-programming method for drift control-affine systems: with a convex control set, it repeatedly linearizes nonlinear costs, dynamics, and state constraints about the previous trajectory and solves a convex linearized optimal-control subproblem, even from an infeasible initial guess . If model error is too large, GuSTO rejects the step and shrinks the trust region; otherwise it accepts and updates the radius, increasing the state-constraint penalty when needed. Under assumptions (A1)–(A4), its iterates converge, up to a subsequence, to a feasible trajectory and control that form a Pontryagin extremal, or terminate at a stationary point [93].

## Comparing the three methods for engineering use

### Guarantees, models, and initialization

**The methods solve different mathematical difficulties.** LCvx is strongest when the important nonconvex constraints admit an exact relaxation. SCvx is strongest when nonlinear dynamics and mission restrictions require repeated approximation. GuSTO supplies a particularly explicit continuous-time framework for control-affine robotic systems, including collision penalties, goal sets, and Pontryagin-based analysis. Their application domains overlap, but their central guarantees are not interchangeable. [5]

| Shared criterion | LCvx | SCvx | GuSTO |
|---|---|---|---|
| Main treatment | Eligible exact relaxation | Successive local approximation | Continuous-time sequential approximation |
| Dynamics scope | Reformulation-compatible models | Broad nonlinear models | Drift control-affine models |
| Original-problem result | Preserved optimum under conditions | Conditional stationarity or local convergence | Pontryagin-stationary limiting result |
| Final time | Often supplied; outer search possible | Optimized through time normalization | Fixed or free within assumptions |
| Main safeguards | Valid relaxation and formulation | Virtual control, penalties, trust regions | Model-error tests, trust regions, state penalties |
| Initial trajectory | Generally unnecessary for exact inner solve | Required reference; feasibility may be relaxed | Required curve; may initially be infeasible |
| Computation pattern | One convex solve per supplied setup | Repeated convex solves | Repeated local solves; optional shooting acceleration |
| Physical demonstration highlighted | Xombie rocket flights | ACL quadrotor flights | Stanford ground free-flyer experiment |

**Global convergence needs careful interpretation.** In nonlinear optimization, a “global convergence” theorem commonly concerns convergence from a broad class of starting points to a stationary point. It does not necessarily mean convergence to a global optimum. This distinction explains how SCvx literature can contain global-convergence claims while still returning initialization-dependent local solutions. LCvx’s exactness claim is different: under its eligibility conditions, relaxation preserves the original optimum. [15][5]

**Feasibility has several separate meanings.** A convex subproblem can be feasible while the original trajectory remains infeasible because of linearized dynamics, virtual inputs, or softened state constraints. A converged numerical trajectory can satisfy constraints at grid points while violating them between those points. Finally, a trajectory feasible for the mathematical model can still be difficult to track on the real vehicle. These distinctions explain why theorem, discretization checks, and physical demonstrations each contribute different evidence. [7]

**Initialization is a design resource.** LCvx’s eligible convex inner solve avoids selecting among nonglobal local minima. SCvx and GuSTO instead use an initial reference to define local models, but can often start from dynamically infeasible guesses. The comparative studies show that reference quality is not a simple monotonic predictor: a physically richer initial trajectory can help, yet it can also lead a local algorithm into a less favorable solution region. [7]

**Combining techniques is often sensible.** The 2017 quadrotor work applies lossless and successive convexification in one planning system. A compatible control restriction can be handled through LCvx while remaining nonconvex dynamics or obstacle geometry is handled successively. Thus, the engineering choice is not always an exclusive selection of one label; it can be a decision about which treatment best matches each source of nonconvexity. [3]

**The comparison favors problem matching.** LCvx offers the strongest exactness result for the narrower covered structure; SCvx and GuSTO gain modeling flexibility by retaining an iterative nonconvex outer problem.

### What the reported runtimes establish

**The literature demonstrates useful computational scales.** By the cutoff, reported results ranged from millisecond trajectory generation to subsecond nonlinear guidance. The table retains the actual statistic and study context rather than treating the figures as a common speed benchmark.

| Algorithm or implementation | Reported time | Statistic or basis | Computing context | Validation context |
|---|---|---|---|---|
| LCvx/G-FOLD custom implementation | Below 200 ms | Development milestone | Customized real-time solver | Powered-descent development |
| LCvx/G-FOLD on Xombie | About 100 ms | Reported onboard divert solve | Xombie flight computer | Rocket flight demonstration |
| LCvx/SCvx ACL examples | 36.5 ms; 122.2 ms | Minimum mean times | Mobile ARM; Intel processors | Quadrotor demonstration scenarios |
| SCvx six-degree-of-freedom landing | Maximum 682 ms | Aggregate solver calls per run | 2.2 GHz Intel Core i7 | Simulation |
| GuSTO free-flyer with shooting | 146 ms | Example total runtime | 4.3 GHz processor | Simulation |
| LCvx with DNN time predictor | 5–8 ms | Reported planning-time range | 2.3 GHz Intel Core i7-10875H | Simulation |
| LCvx EAGLE guidance prototype | Expected below 800 ms | Typical onboard expectation | EAGLE onboard computer | Simulation-based assessment |

Sources are the G-FOLD report [5], ADAPT demonstration [13], ACL paper [3], SCvx landing paper [7], GuSTO paper , DNN-LCvx study [8], and EAGLE thesis [11].

**A small mean does not guarantee deadlines.** A minimum mean time describes favorable average performance among tested configurations. A maximum measured over a finite collection of runs describes that collection. Neither statistic, by itself, proves a worst-case execution-time bound for all admissible flight states, processor loads, or outer-loop behaviors. Real-time suitability depends on the timing requirement of the actual guidance function.

**The planning deadline is mission-specific.** A drone tracking controller may operate much faster than its trajectory generator. Likewise, a rocket can compute a new landing trajectory and then track it using a separate control loop. The 2017 ACL experiments explicitly illustrate this separation by computing the translational trajectory at maneuver onset. Comparing planner milliseconds with an attitude-control update period would therefore confuse two different system functions. [3]

**Accuracy and model scope consume computation.** The \(5\)–\(8\ \mathrm{ms}\) DNN-assisted result uses a learned duration estimate and a compatible three-degree-of-freedom optimization. The subsecond SCvx result includes rotational dynamics, aerodynamic options, and conditional constraints. Their numerical difference reflects different optimization tasks and design choices, not merely the names LCvx and SCvx. [8][7]

**Processor labels are insufficient for ranking.** The ACL paper’s favorable ARM and Intel means arise from a series of processors and example configurations. Those figures do not establish that an arbitrary mobile ARM processor outperforms an arbitrary Intel processor. Similarly, GuSTO’s desktop simulation timings should be interpreted in their stated computational environment rather than transferred directly to a radiation-tolerant flight computer. [3]

**The computational judgment is conditional.** Convex structure and solver customization can make demanding trajectory generation practical onboard, but the entire configured algorithm—not its fastest published inner solve—must satisfy the vehicle’s deadline.

### Selecting a method for landers, drones, and robots

**For structured landing, start with LCvx.** If the mission can be represented by compatible powered-descent dynamics, eligible thrust and pointing constraints, and an acceptable duration-selection mechanism, LCvx offers an unusually attractive combination of exactness and flight-tested implementation. Its value is greatest when those assumptions reflect the physical vehicle closely enough that a more general nonlinear optimizer adds complexity without changing the feasible maneuver substantially.

**For coupled landing, favor SCvx.** When attitude evolution, aerodynamic lift and drag, ignition timing, or state-triggered restrictions determine the maneuver, SCvx has a more directly demonstrated modeling path. The 2020 work shows why those additional degrees of freedom matter, while also making the computational and convergence trade-offs explicit. The recommendation depends on successfully driving dynamic defects and artificial actuation to the required tolerances within the available planning interval. [7]

**For cluttered robot planning, consider GuSTO.** Control-affine systems with collision restrictions and terminal goal sets fit GuSTO’s formulation particularly well. Its state-penalty mechanism and initialization experiments are relevant when a convenient starting curve intersects obstacles, and its multiplier-based acceleration can be valuable when high-accuracy refinement is expensive.

**For drones, separate geometry from dynamics.** A planner dominated by an eligible nonconvex control envelope may benefit from LCvx, as the agile-flip demonstration shows. A planner dominated by coupled motion, changing restrictions, or cooperative passage geometry may justify SCvx. A control-affine drone model with goal-set and collision-planning requirements can motivate GuSTO. The deciding question is which mathematical difficulty dominates, not whether the platform is called a drone. [3][14][21]

**Application maturity should remain platform-specific.** LCvx’s Xombie record directly demonstrates onboard optimization during terrestrial rocket flight. SCvx’s quadrotor demonstrations establish physical aerial execution, while its richer rocket models remain computational studies in the examples described here. GuSTO’s Stanford experiment establishes physical ground execution of a spacecraft-like maneuver. None of these evidence levels is a substitute for another simply because the vehicles share a broad aerospace application.

**The named rocket answer is Masten.** For a concrete company-and-rocket example, G-FOLD on Masten Space Systems’ Xombie is the strongest supported attribution in this survey. SpaceX Falcon 9 appears in related landing literature as motivation for reusable-launcher autonomy, but that contextual mention is not an algorithm-specific attribution to LCvx, SCvx, or GuSTO. The same discipline separates NASA Astrobee’s operational ISS role from GuSTO’s Astrobee-like simulations. [2][11]

**Evidence uses distinct measurement bases.** Application labels describe the reported study, and research demonstrations do not by themselves establish algorithm-specific operational deployment. Timings retain each paper’s hardware, statistic, model, and solver scope; the EAGLE onboard figure is a published expectation. Explicit arithmetic, such as sample totals and rounded runtime reductions, is derived from the stated inputs. Xombie counts from different reports are kept separate rather than summed, and repository links identify software examples rather than additional dated flight milestones. Historical judgments are limited to evidence available by 31 December 2022.

**The final choice follows the nonconvexity.** Use LCvx where exact relaxation is justified, SCvx where nonlinear vehicle and mission modeling warrants iterative optimization, and GuSTO where its control-affine robot formulation and continuous-time analysis fit the task. Their shared achievement by the end of 2022 was making constrained optimization a credible onboard planning tool; their differences determine how much of that credibility comes from exact reformulation, conditional convergence, or demonstrated physical execution.

## Appendix: Further Evidence

**Additional documented evidence**

**Source map and audit**

The map uses independent permitted records and preserves each source’s evidence level. **LCvx** is anchored by NASA/JPL’s **1 December 2011** Tech Brief on Mars minimum-landing-error guidance: lossless convexification, two SOCPs, and a technical scenario are documented, but not flight or deployment [98]; Lu and Liu’s **25 April 2014** paper supplies a separate aerospace record [99]. **SCvx (Successive Convexification)** is mapped to the **2018** Mars 6-DoF paper, whose evidence is 2-D/3-D simulation [43], and the **11 June 2019** Apollo rendezvous study, explicitly an offline trade-study result . **GuSTO** is mapped to the **2019** ICRA publication listed by NASA [50]; a **2021** thesis connects it to spacecraft robotic manipulation and Astrobee hardware results, but reports no separate application date [95].

Dates are labeled as publication, application, demonstration, test, deployment, flight, or mission dates and checked against **2022-12-31**; missing organization, platform, confidence, and event-date cells remain unknown. The denylisted tutorial and five URLs were blocked from scouting through editing; accidental exposure was quarantined and contributed no facts, citations, metadata, or quotations. Mirrors, indexes, and unrelated hits were rejected. Uppercase **GUSTO** is a NASA astronomy observatory, not GuSTO; its 2022 record planned a **December 2023** launch, so it is a name-collision exclusion [97].


Cutoff-compliant leads include an LCvx-related source dated 25 Apr 2014, GuSTO references from 2019 and 2022, and an SCvx 2018 Mars 6-DoF simulation [273, 411, 250]. January 2026 and April 2025 sources fall after the 2022 cutoff; GUSTO astronomy sources are unrelated to GuSTO, and exclusion of the prohibited tutorial/URLs is not explicitly documented [275, 265, 425, 218, 237].

## References

[1] <https://doi.org/10.1007/s42064-017-0003-8> Aerospace convex-optimization survey; Liu, Lu, and Pan’s 2017 survey
[2] <https://doi.org/10.2514/1.G000399> G-FOLD flight demonstration; LCvx attribution and flight tests; Eight-flight implementation record; Xombie attribution
[3] <https://doi.org/10.1109/iros.2017.8206363> Quadrotor flight demonstrations; Onboard quadrotor architecture; LCvx-enabled quadrotor flip; 2017 quadrotor flight demonstrations; Quadrotor flight and proces…
[5] <https://govindchari.com/assets/pdf/gfold_paper.pdf> G-FOLD landing motivation; G-FOLD formulation and proof summary; G-FOLD control constraints; Slack-variable lifting in G-FOLD; Maximum-principle argument; Rela…
[7] <https://doi.org/10.2514/1.g004549> SCvx discretization and implementation; Six-degree-of-freedom guidance motivation; 2020 powered-descent formulation; Virtual-control penalties and termination;…
[8] <https://doi.org/10.3390/app12073383> 2022 powered-landing study; 2022 free-final-time analysis; LCvx variable substitution; LCvx transcription to SOCP; Approximation discussion in the 2022 study;…
[9] <https://doi.org/10.2514/1.g001480> Powered-descent SOCP implementation; Customized real-time interior-point methods; LCvx extensions and real-time guidance
[10] <https://doi.org/10.1631/fitee.1900458> Powered-landing survey; Mars-landing development
[11] <https://elib.dlr.de/118732/1/MasterthesisAWENZEL.pdf> EAGLE implementation assessment; EAGLE simulation and timing assessment; Falcon 9 context in the EAGLE thesis
[12] <https://www.nasa.gov/centers-and-facilities/armstrong/successful-test-flights-for-mars-landing-technology/> NASA description of Xombie and G-FOLD; NASA’s integrated ADAPT demonstration
[13] <https://doi.org/10.1109/aero.2014.6836462> ADAPT onboard divert demonstration
[14] <https://doi.org/10.1109/iros40897.2019.8967706> Compound STCs for quadrotors; Compound-STC simulation results; Compound-STC quadrotor scenarios
[15] <https://digital.lib.washington.edu/researchworks/items/86655236-a822-4188-a050-229f15f9f118> Mao’s 2021 dissertation; SCvx convergence discussion
[16] <https://ar5iv.labs.arxiv.org/html/2208.07259> 2022 corridor-planning discussion
[17] <https://doi.org/10.2514/6.2018-0617> 2018 free-final-time study
[18] <https://doi.org/10.1109/access.2021.3120840> SCvx rocket-ascent simulations
[19] <https://doi.org/10.1109/aero53065.2022.9843495> 2022 visual modeling and flight experiments
[20] <https://github.com/StanfordASL/GuSTO.jl>
[21] <https://github.com/StanfordASL/GuSTO_quad_astrobee> GuSTO simulation examples; GuSTO companion simulations
[22] <https://www.nasa.gov/astrobee/> NASA Astrobee milestones
[23] <https://doi.org/10.6028/nist.ir.7262>
[24] <https://publications.ri.cmu.edu/storage/publications/pub_files/2012/5/ICRA12_xuwd_Final.pdf>
[25] <https://par.nsf.gov/servlets/purl/10354182>
[26] <https://doi.org/10.3390/s18072185>
[27] <http://hdl.handle.net/10467/76763>
[28] <https://ar5iv.labs.arxiv.org/html/1609.05243>
[29] <https://www.europarl.europa.eu/RegData/etudes/etudes/join/2013/410220/EXPO-DROI_ET(2013)410220_EN.pdf>
[30] <https://www.mdpi.com/1424-8220/18/7/2185>
[31] <https://ddl.stanford.edu/sites/g/files/sbiybj25996/files/media/file/from_the_racetrack_to_the_road_real_time_trajectory_replanning_for_autonomous_driving_0.pdf>
[32] <https://depts.washington.edu/uwrainlab/wordpress/wp-content/uploads/2020/01/AIAA_SciTech_2020.pdf>
[33] <https://arxiv.org/html/1802.03827v1>
[34] <https://digital.lib.washington.edu/bitstreams/15d85c10-f2da-4abb-9612-9e1d58244bef/download>
[35] <https://skoge.folk.ntnu.no/prost/proceedings/ifac2014/media/files/2736.pdf>
[36] <https://ar5iv.labs.arxiv.org/html/1701.00558>
[37] <https://doi.org/10.48550/arxiv.2201.09455>
[38] <http://www.larsblackmore.com/AcikmeseBlackmoreAutomatica10.pdf>
[39] <https://arxiv.org/html/1911.09013>
[40] <https://arxiv.org/html/1804.06539v2>
[41] <https://digitalcommons.calpoly.edu/cgi/viewcontent.cgi?article=1245&context=eeng_fac>
[42] <https://doi.org/10.1145/1721695.1721698>
[43] <https://doi.org/10.2514/6.2018-0617>
[44] <https://ieeexplore.ieee.org/document/8206363>
[45] <https://ar5iv.labs.arxiv.org/html/1902.02726>
[46] <https://ifatwww.et.uni-magdeburg.de/ifac2020/media/pdfs/3780.pdf>
[47] <https://arxiv.org/html/1902.02726>
[48] <https://arxiv.org/abs/1804.06539v1>
[49] <https://axi.lims.ac.uk/paper/1804.06539>
[50] <https://www.nasa.gov/astrobee-research-publications/>
[51] <https://digital.lib.washington.edu/server/api/core/bitstreams/3d9f16b0-2287-4b13-8690-99c8c6370caa/content>
[52] <http://larsblackmore.com/BlackmoreEtAlACC2012.pdf>
[53] <https://ieeexplore.ieee.org/abstract/document/6314722>
[54] <https://www.grafiati.com/en/literature-selections/lossless-convexification/>
[55] <https://github.com/Natsoulas/lcvx-pdg>
[56] <https://nicholasnatsoulas.com/files/ASEN_6020_LCVX_Soft_Landing_Project_Natsoulas.pdf>
[57] <https://doi.org/10.1016/j.sysconle.2012.04.010>
[58] <https://doi.org/10.1109/acc.2011.5990959>
[59] <http://larsblackmore.com/BlackmoreEtAlJGCD10.pdf>
[60] <https://elib.dlr.de/118732/1/MasterthesisAWENZEL.pdf>
[61] <https://doi.org/10.3390/app12073383>
[62] <https://github.com/Planetary-Soft-Landing-at-Purdue/PSL-with-KSP>
[63] <https://portal.mardi4nfdi.de/wiki/Lossless_convexification_of_a_class_of_optimal_control_problems_with_non-convex_control_constraints>
[64] <https://ntrs.nasa.gov/citations/20140001972>
[65] <https://www.ce.cit.tum.de/fileadmin/w00cgn/air/Personal_Files/YuanfeiLin/MAGRSCvx_STL.pdf>
[66] <https://dl.acm.org/doi/abs/10.1109/ITSC45102.2020.9294698>
[67] <https://arxiv.org/html/2010.06276v1>
[68] <https://par.nsf.gov/servlets/purl/10377628>
[69] <https://avokloti.github.io/files/successive_convexification.pdf>
[70] <https://doi.org/10.1109/cdc.2017.8263811>
[71] <https://depts.washington.edu/uwrainlab/wordpress/wp-content/uploads/2018/12/p3_main.pdf>
[72] <https://ntrs.nasa.gov/api/citations/20230009811/downloads/NASA-TM-20230009811.pdf>
[73] <https://hal.science/hal-04968935v1/file/18223-IAC_22_C1.4.x73177_final.pdf>
[74] <https://www.lysandrou.com/projects/scvx.pdf>
[75] <https://arxiv.org/abs/1804.06539>
[76] <https://digital.lib.washington.edu/researchworks/items/86655236-a822-4188-a050-229f15f9f118>
[77] <https://doi.org/10.48550/arxiv.1804.06539>
[78] <https://arxiv.org/abs/2112.00108>
[79] <https://www.alphaxiv.org/@michael-miki-szmuk>
[80] <https://www.alphaxiv.org/audio/1802.03827>
[81] <https://doi.org/10.2514/1.a35461>
[82] <https://ar5iv.labs.arxiv.org/html/2112.00108>
[83] <https://arxiver.lazybrains.com/author/758135/page/1>
[84] <https://stanfordasl.github.io/wp-content/papercite-data/pdf/Banerjee.Lew.Bonalli.ea.AeroConf20.pdf>
[85] <https://stanfordasl.github.io/wp-content/papercite-data/pdf/Bonalli.Cauligi.Bylard.Pavone.ICRA19.pdf>
[86] <https://ieeexplore.ieee.org/document/8794205>
[87] <https://thz.mit.edu/wp-content/uploads/2022/03/A_Tunable_Unidirectional_Source_for_GUSTOs_Local_Oscillator_at_4.74_THz.pdf>
[88] <https://www.emergentmind.com/topics/sequential-convex-programming>
[89] <https://dl.acm.org/doi/10.1109/ICRA.2019.8794205>
[90] <https://ieeexplore.ieee.org/abstract/document/8794205/>
[91] <https://github.com/UW-ACL/SCPToolbox.jl/compare/master...csm>
[92] <https://github.com/nurkenkz/Gusto.m>
[93] <https://stacks.stanford.edu/file/druid:mx142wx7479/Cauligi-augmented.pdf>
[94] <https://github.com/StanfordASL/GuSTO.jl/blob/master/README.md>
[95] <https://purl.stanford.edu/mx142wx7479>
[96] <https://cseweb.ucsd.edu/~kastner/papers/phd-thesis-irturk.pdf>
[97] <https://doi.org/10.1117/12.2629051>
[98] <https://ntrs.nasa.gov/citations/20120001230>
[99] <https://arc.aiaa.org/doi/10.2514/1.62110>
