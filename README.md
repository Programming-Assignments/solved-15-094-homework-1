Download Link: https://assignmentchef.com/product/solved-15-094-homework-1
<br>
<span class="kksr-muted">Rate this product</span>

1 Robust Reformulation

Consider the following constraint on x, where z is an uncertain parameter: (2 + z)x ≤ 1.

This constraint is equivalent to the following formulation, when there is no uncertainty in z.

(2 + z)x + s = 1,

s ≥ 0.

Now think of the robust counterparts of these two sets of constraints. The uncertainty set is the interval {z : |z| ≤ 1}.

1.1

Find the feasible sets of the above formulations. Are they equal? What can you say about robust formulation of constraints?

1.2

Now, consider the following reformulation: (2+z)x+s(z)=1, ∀z:|z|≤1,

s(z)≥0, ∀z:|z|≤1.

Here the difference is that the slack variable introduced is an arbitrary function of uncertain parameter z. Find the feasible set, and compare it with the previous result.

2 MI/LP Modeling

Model the following using LP/MILP compatible big-M constraints. There is no need to indicate values for M, but please indicate the subset of real numbers to which variables belong (eg. integers Z etc.).

1

2.1

|2×1 − 3×2| ≥ 6 2.2

|x1 + 2×2| ≤ 4 (Do not use integer variables here.) 2.3

x1 and x2 are integer variables. If x1 ≤ 4, x2 ≥ 5. 2.4

x1, x2 are continuous. Either x1 + 4×2 ≤ 7 or 2×1 + 3×2 ≥ 4 are satisfied, but not both.

2.5

x is integer, but not equal to 3.3 Computational Tools

15.094 will have a significant practical component to complement the theory. To facilitate your implementation of RO, we will be leaning on JuMPeR.jl, a modeling language for robust optimization that couples with JuMP.jl.

We strongly urge you to complete these setup instructions in advance of the first recitation, in case issues crop up. Please make sure that you have the specific versions of the required software, since JuMPeR.jl is incompatible with more recent versions of most Julia packages. Please install packages in the given order as well.

3.1 Installation

3.1.1 Install Julia-1.0.5.

Download and install julia-1.0.5 by following the instructions here: https://julialang.org/downloads/

3.1.2 Install Gurobi 8.1.

Register, download and install Gurobi 8.1, with a free academic license: https://www.gurobi.com/downloads/gurobi-software/

If you have trouble locating your license information, please refer to the Gurobi account page while logged in:

<blockquote class="wp-embedded-content" data-secret="EUzVqVJFDt">

 <a href="https://www.gurobi.com/account/">My Account</a>

</blockquote>

<iframe sandbox="allow-scripts" security="restricted" style="position: absolute; clip: rect(1px, 1px, 1px, 1px);" title="“My Account” — Gurobi" data-secret="EUzVqVJFDt" width="600" height="338" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" data-src="https://www.gurobi.com/account/embed/#?secret=EUzVqVJFDt" class="wp-embedded-content lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw=="></iframe>

2

3.1.3 Install git.

Install git (if you don’t have it already): https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

Git will allow us to update environments for you in real time, in case you need new software for the problem sets. If Git is new to you, we encourage you to check out this tutorial: https://git-scm.com/docs/gittutorial

3.2 Installing needed of Julia packages.

Clone this repo into the directory of your choice: https://github.com/1ozturkbe/15094code

In your terminal, go inside the 15094code/ directory, and open the Julia project using the following command: julia –project=.

This will open a Julia REPL and initialize the Julia environment (described by 15094code/Project.toml) in the current directory, that will allow you to maintain a specific version of the required packages. Type in the following code to instantiate the packages: using Pkg; Pkg.instantiate()

Note that, to access the above packages, you will need to always access Julia through julia –project=directory-to-15094code. This way, the packages you Pkg.add to the generic julia1.0.5 environment should not interfere with the versions installed in 15094code/Project.toml. We have initialized versions of packages you may need to complete future problem set questions and the final project. Feel free to update and change them through the semester, but know that you can always revert to this working version.

3.3 Testing the installation.

Please run examples/portfolio.jl either inside your REPL or by typing the following into your terminal: julia –project=. examples/portfolio.jl.

This is an example problem from JuMPeR, and will test your Julia environ- ment for 15.094. If run properly, it should return a table of statistics of portfolio returns for a random portfolio optimization problem, where Γ is the risk budget. You will need to debug your installation if you get an error.

3.4 Check out the JuMPeR tutorial.

In 15094code, we have included an updated version of the JuMPeR tutorial that Iain developed. This will help you get used to the syntax of JuMPeR (if you are

3

not familiar with JuMP already). It is located in examples/JuMPeR tutorial.ipynb, which is a notebook file. You can access the notebook by calling jupyter notebook from the code directory.

If the command doesn’t work, you may need to do a separate install of Python Anaconda. Otherwise, you should be able to select Julia-1.0.5 as your kernel, and run the code cell by cell.

3.5 Writing a robust knapsack problem.

Using your newly acquired knowledge of JuMPeR, please write a robust version of the binary knapsack problem under ellipsoidal uncertainty.

maximize c′xs.t.(a+ ̃a)′x≤b, ∀a ̃: ||a ̃||2 ≤ρ

xi ∈ {0,1}, i = 1,…,n

Please use n = 20, b = 4, and randomly generated ai, ci ∈ [0,1]. Include your code, as well as a plot of the optima for a relevant range of ρ. Assuming you were using this problem to maximize the revenue of a cargo aircraft subject to weight capacity, please use your intuition and knowledge of Gaussian prob- abilities to suggest a ρ that provides a good tradeoff between robustness and optimality.

As always, please come to office hours if you have hiccups with the above.