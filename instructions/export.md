# Exporting

---

To 3D print a PCB using a printer that supports dual extrusion with conductive and non-conductive filaments, you’ll need to accurately separate the PCB design into two distinct parts: the substrate (non-conductive part) and the traces (conductive part). Here’s a step-by-step guide on how to export your KiCad project into separate OBJ files for the substrate and the traces:

Step 1: Preparing the PCB in KiCad

	1.	Open Your PCB Layout in KiCad:
	•	Launch KiCad and open your project.
	•	Open Pcbnew, which is the PCB layout editor in KiCad.
	2.	Set Up the Layers:
	•	Ensure that your PCB design is complete and that all the layers (copper, silkscreen, etc.) are properly defined.
	•	Make sure the copper layers (traces) are correctly laid out, as these will be your conductive paths.

Step 2: Exporting the PCB Design

Exporting the Substrate (Non-Conductive Part)

	3.	Export the Board Shape:
	•	Go to File > Export > STEP....
	•	In the export options, deselect all copper layers and any other conductive elements.
	•	Export only the board shape and any non-conductive components.
	•	Save the file as pcb_substrate.step.

Exporting the Metal Traces (Conductive Part)

	4.	Export Copper Layers to VRML:
	•	Go to File > Export > VRML....
	•	In the export options, select only the copper layers.
	•	Save the file as pcb_traces.wrl.

Step 3: Converting Files to OBJ

Using FreeCAD for the Substrate

	5.	Convert STEP to OBJ (Substrate):
	•	Open FreeCAD and import the pcb_substrate.step file (File > Open).
	•	Switch to the Part workbench.
	•	Select the model and go to Part > Create shape from mesh... to create a mesh.
	•	Switch to the Mesh Design workbench.
	•	With the shape selected, go to Meshes > Create Mesh from Shape....
	•	Export the mesh as an OBJ file (File > Export... and select OBJ format).
	•	Save the file as pcb_substrate.obj.

Using Blender for the Traces

	6.	Convert VRML to OBJ (Traces):
	•	Open Blender and import the pcb_traces.wrl file (File > Import > X3D/VRML (.x3d/.wrl)).
	•	With the model imported, ensure it’s properly oriented and scaled.
	•	Export the model as an OBJ file (File > Export > Wavefront (.obj)).
	•	Save the file as pcb_traces.obj.

Step 4: Preparing for Dual Extrusion 3D Printing

	7.	Combining and Aligning in Blender:
	•	Import both pcb_substrate.obj and pcb_traces.obj into Blender.
	•	Align the traces with the substrate. They should fit perfectly if the exports were done correctly.
	•	You may want to separate them into different layers or objects for clarity.
	8.	Export Combined Model:
	•	If your 3D printer’s software requires a single file with different materials, export the combined model from Blender.
	•	Otherwise, keep them as separate OBJ files and load them into your slicer software.

Step 5: Printing

	9.	Loading Files into Slicer Software:
	•	Open your 3D slicer software that supports dual extrusion.
	•	Import both pcb_substrate.obj and pcb_traces.obj.
	•	Assign the non-conductive filament to the substrate and the conductive filament to the traces.
	10.	Configure Print Settings:
	•	Adjust the print settings for each material (e.g., temperature, speed).
	•	Ensure the slicer aligns both models perfectly for the dual extrusion process.
	11.	Print Your PCB:
	•	Start the print job and monitor the process to ensure that both materials are being extruded correctly.

Additional Tips

	•	Calibration: Ensure your dual-extrusion printer is well-calibrated for both filaments.
	•	Conductive Filament Handling: Conductive filaments may have specific handling requirements; follow the manufacturer’s recommendations.
	•	Post-Processing: After printing, you might need to perform some post-processing, such as soldering components to the conductive traces.

By following these steps, you should be able to export your KiCad project into separate OBJ files for the substrate and metal traces, and then print them using your dual-extrusion 3D printer with conductive and non-conductive filaments.
