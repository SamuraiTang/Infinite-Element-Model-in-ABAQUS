# Infinite-Element-Model-in-ABAQUS

1. Build the Finite Element model through ABAQUS;

2. During the meshing, we need to set the corresponding area to the "Sweep" mode. Meanwhile, please adjust the sweep path and direction;

3. Switch the element type of the objective elements to something else, whose element nodes are no less than those in the final infinite element;

4. Run the simulation to make sure the model is feasible;

5. Save the INP file, rename and open it;

6. Search the objective elements and change the element type (e.g. change CPE8R to CINPE5R);

7. Import the infinite model into the ABAQUS;

8. Release the corresponding boundary conditions;

9. Reselect the nodes for the Set "ALLNODES" since the

10. if the stiffness matrix is required, please insert the modified command into the keywords:
          **
    
          *STEP
    
          *MATRIX GENERATE, STIFFNESS, SOLID INFINITE FORMULATION=STATIC, ELSET=ALLELE
    
          *MATRIX OUTPUT, STIFFNESS, FORMAT=MATRIX INPUT
    
          *END STEP

12. Run the simulation using the 
