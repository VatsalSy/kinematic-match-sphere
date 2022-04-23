# Kinematic Match: The case of a rigid sphere and an elastic membrane
This repository serves a supplementary material for [this article](google.com). Here we provide code in Julia, Matlab and Python to simulate an axis-symmetric impact between a rigid sphere and an thin elastic membrane.


<p align="center">
  <img width="460" height="300" src="https://user-images.githubusercontent.com/51973026/164895999-b7d0b276-0552-4798-adba-aeb5138f92dd.gif">
</p>

## Usage

All three languages have a main script, called `solveMotion`, and the initial conditions of the impact can be passed as name-value pairs. Parameters corresponding to the simulation analyzed in detail in the article are run by default when `solveMotion` it's called with no arguments. 

Both the Julia and Matlab versions are decently documented and offer good performance. Although the python version is up and running, it currently does not pre-allocate the matrices to solve the linear system, which makes it impractical to use for comparisons with experiments.

Here's a sketch of the most important parameters that can be set by `solveMotion`

```julia
julia> include("solveMotion.jl") # This is not necessary in matlab and python
julia> solve_motion(
       rS =  2.38, # Sphere radius in (mm)
       Tm =   107, # Membrane linear tension in (Pa * m)
       z_k =  3.0, # Initial position of the center of the sphere, in (mm)
       v_k = -0.5, # Sphere's initial velocity in (m/s)
       N =    100, # Number of points on the membrane in the discretized problem per unit radius 
       plotter = false, # Whether to plot a 2D real-time snapshot of the simulation (false is best for performance)
       export_data = true, # Whether to export simulation final results. 
                           # In Julia, a single jld2 file is created and a reference to this file is stored in a .csv
)
```

Other parameters are available, see the documentation inside the Matlab or Python versions. Also, please note that syntax may vary  

This project follows [the following](https://towardsdatascience.com/how-to-keep-your-research-projects-organized-part-1-folder-structure-10bd56034d3a) folder structure, so all files generated by solveMotion will be stored in `../2_pipeline/solveMotion/out/example_file.jld2`


## TODO

- [ ] Implement sparse matrices on Python
- [ ] Standarize variable names across three projects. 
- [ ] Include scripts used to generate the plots of our article.
- [ ] Benchmark all three versions.


## Cite this work

If you find this piece of software useful, you can cite our work as 

