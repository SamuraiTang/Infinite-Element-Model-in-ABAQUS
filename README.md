# Infinite-Element-Model-in-ABAQUS

1. Build the Finite Element model through ABAQUS;

2. During the meshing, we must set the corresponding area to the "Sweep" mode. Meanwhile, please adjust the sweep path and direction;

3. You should mesh the infinite area in the end, avoiding the nodal label going to be eliminated occurring in the finite element;

4. Switch the element type of the objective elements to something else whose element nodes are no less than those in the final infinite element;

5. Run the simulation to make sure the model is feasible;

6. Save the INP file, rename and open it;

7. Search the objective elements and change the element type (e.g. change CPE8R to CINPE5R);

8. Import the infinite model into the ABAQUS;

9. Release the corresponding boundary conditions;

10. Do not Reselect the nodes for the Set "ALLNODES" since the ABAQUS will change the element connectivity automatically;

11. Create a new assembly set containing all the infinite elements (usually named "INFI");

12. if the stiffness matrix is required, please insert the modified command into the keywords:
          **
    
          *STEP
    
          *MATRIX GENERATE, STIFFNESS, SOLID INFINITE FORMULATION=STATIC, ELSET=ALLELE
    
          *MATRIX OUTPUT, STIFFNESS, FORMAT=MATRIX INPUT
    
          *END STEP

13. Run the simulation using the infinite model;

14. Double-check the element connectivity and the results, and calculate the actual number of nodes;

15. Run the script to generate all the input matrices.
