# Meeting with Mary  
- We should start with the Chemical Aqueous Phase Radical Mechanism(CAPRAM) 4.0 to check the aqueous chemistry rates for the three reactions. 
- Then we could do the same as we did to the heterogeneous reactions like the N2O5 + H2O 
but need to replace some parameters like the surface area of aerosol to the equivalent surface liquid surface, 
since the aqueous chemistry we want to add happens in the cloud water droplets’ absorption, not the aerosol phase reactions  

# Meeting with Simone
- Becky’s high NOx scheme on the SOA might work differently with the high NOx chemistry of Kasting’s one. 
- The high NOx scheme in Becky’s scheme could be just an environment for SOA, it could not end up not removing any of those NOx.  
However, Becky also did a lot of modifications to the scheme, so it is not sure whether it could work or not
- See soot absorbs light, and how they affect the photolysis. 
- How long took HCl and HBr to get removed?  
  a.	Condensations of halogens
  b.	Injections of sea water; it could be that the splashed sea water to remove halogens. They will be precipitated back to ocean
  c.	Soot heat stratosphere after get removed, it get cooled and rain out in the form HNOx, it happens in stratosphere  
- We need to know the surface area of liquid. And we need to know the whole surface area of liquid to fix the heterogeneous chemistry. 
However, this is not included in Simone’s model, and her model is not stable.
- Also, we might also need to know how much coating the soot should have to have heterogeneous chemistry reactions with liquid. It works just like above. 
So the surface coating area of organic aerosol could affect its heterogeneous reactions with liquid.  

# Meeting with Becky
- The uptake of NOx by Aerosols could be important. And she thinks that it might be okay to use the latest JPL rates.  We could assume that NOx is being absorbed
- She thinks that the sensitivity test on coating of sulfates could not that important
- More info is included in her email. Compilation of Henry’s law constant etc

# Detailed Plan
- control run
- perturbation run
- TUV control run
- TUV perturbation run 
- Add the regime for air heating sources of NO

# Adding Below Reactions:
-	N2O5 + Soot (carma/base/oxidgas.F90)		        (aerosol uptake)
-	NO2 + Soot (carma/base/oxidgas.F90) 		        (aerosol uptake)
-	Add N2O4, HONO as a new species.
-	Dry/Wet removal of N2O5, N2O4, HONO(probably need to change the in the sourcecode..., the way that they are trying to calculate probably will not recognize them)  
-	N + O3 --> NO+O2					           (Standard NOx)
-	NO2 + H --> OH + NO				           (Standard NOx)
-	NO + OH + M --> HNO2 + M			          (Standard NOx)
-	NO+NO+O2 --> 2NO2				          (High NOx)
-	NO+NO2+O2-->NO2+NO3 				          (High NOx)
-	NO2+NO2+M-->N2O4 + M                                                (High NOx)
-	N2O4+M-->2NO2+M                      			          (High NOx)
-	N2O4 + H2O-->HONO +HNO3 			           (Aqueous Chemistry)
-	NO2 + H2O --> 0.5HONO + 0.5HNO3		          (Aqueous Chemistry)
-	NO + NO2 + H2O --> 2HNO2                                             (Aqueous Chemistry)
-	3NO2 + H2O --> 2HNO3 + NO			           (Aqueous Chemistry)

