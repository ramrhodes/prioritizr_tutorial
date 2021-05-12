# `prioritizr` tutorial
# authors: Anna Abelman, Vanessa Rathbone & Rachel Rhodes

------------------





------------------
## The goal
This tutorial provides a short example to get you familiar with the prioritizr R package which can be used to build and solve conservation planning problems. This tool can be used to produce a resproducible spatial prioritization model in R. Similar to the spatial prioritization tool Marxan, the underlying objective of prioritizr is to design reserves (or areas) that achieve a conservation goal while minimizing costs. 

More information can be found here: https://prioritizr.net/


## Why use prioritizr?
In prioritizr, the problem objective defines the overall goal of the conservation plan. This can be done a number of ways including using a minimum set objective which minimizes the cost of a reserve network, while ensuring all targets are met; maximum features objective, which fulfills as many targets as possible within a specific budget; maximum phylogenetic diversity objective which maximizes phylogenetic diversity of features within a specific budget; and more.

Prioritizr is a great spatial planning tool that can help inform decisions on how and where to focus conservation efforts given limited resources. Prioritizr can identify, map, and prioritize sites or areas based on specific goals, targets and costs. 


## What you'll need
You'll need 6 inputs to run your prioritizr model, they include: 

1) *Planning Unit:* The planning unit layer are spatial sub-units of the entire planning area
2) *Conservation Features:* Features you'll be setting your targets for like, species distribution ranges, critical habitat, etc.
3) *Targets:* The percent of the conservation features you aim to prioritize
4) *Constraints:* Any sort of data or features we would want to lock in or lock out of the designs. 
5) *Connectivity:* Determine the fragmentation of your reserve design by including a boundary length modifier/boundary penalty 
6) *Costs:* The cost layer specifies the cost of including each planning unit in the reserve system.


### Obtain Gurobi license 
To run prioritizr you will need to use an optimization tool or algorithm solver. Gurobi is a widely used option and is available for free use under an academic license. Follow the tutorial on how to obtain a license and how to install the optimizer onto your MAC or PC. You won't be able to run prioritizr without an optimization tool installed on your machine. More information can be found here: https://www.gurobi.com/

Below is a step by step guide to obtaining a free Gurobi academic license & installation instructions:

Step 1. Register on Gurobi website as Acedemic user: https://pages.gurobi.com/registration

Step 2. Once logged in, navigate to https://www.gurobi.com/free-trial/

Step 3. Click 'Academic Users: Request a Free Academic License'

Step 4. Click 'Download Gurobi Optimizer' page

Step 5. Download and install 'Gurobi Optimizer'

Step 5. Navigate back to 'Download Gurobi Optimizer Page (https://www.gurobi.com/downloads/) and in the section **Request a License**, click 'Academic License & follow installation instrucrtions

### R Packages
Here are some packages you may need to run a spatial prioritization:

library(raster) - to rasterize shapefiles
library(tidyverse)
library(sf) - for special features (adding geometry)
library(here) - file organization 
library(fasterize) - to format rasters with existing rasters CRS and extents
library(stringr)
library(janitor) - to update dates
library(prioritizr) - to run prioritizr
library(rgdal) - 
library(gurobi) - to run spatial optimizer Gurobi