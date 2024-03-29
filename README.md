# OpenTronsOT2SMACK
Resource for the OpenTrons OT-2 robot in the SMACK lab (smack-lab.com)

### Terms and definitions: 
  <ins>**OT-2 Python protocol file**</ins> - the python file (.py) that is to be imported into the OpenTrons OT-2 robot.

  <ins>**Jupyter Notebook file**</ins> - the Jupyter Notebook file (.ipynb) that is to be used to generate the interpretable Python dictionary variables that are to be pasted into the OT-2 Python protocol file.

  <ins>**source plate** </ins> - the plate that contains the unnormalized DNA.

  <ins>**destination plate** </ins> - the plate that will contain the normalized DNA.

  <ins>**source well** </ins> - the source plate well containing the DNA that will be normalized.

  <ins>**destination well** </ins> - the destination plate well that will contain the normalized DNA upon the completion of this protocol.

  <ins>**water volume** </ins> - the volume of water to be added to the destination well to obtain adequate normalization. Calculated by the user in conjunction with DNA volume.

  <ins>**dna volume** </ins> - the volume of DNA that is to be added to the destination well to obtain adequate normalization. Calculated by the user in conjunction with water volume.

# Normalization
This is a protocol designed for the use of normalizing DNA that is to be used for sequencing. Different volumes can be used for water, dna, and the destination well can be edited. 
## Standard operating procedure for Normalization
<ins>Prereq:</ins> 

Jupyter Noteboooks needs to be installed on the computer that will generate the python (.py) command script for the OT-2: https://jupyter.org/install. If this is your first time installing jupyter notebooks, you may need to install python on your machine prior.

You will also need the OpenTrons software: https://opentrons.com/ot-app/

<ins>Protocol:</ins>

1. Create an input comma-separated values file (.csv) that contains the source well, destination well, water volume, and dna volume information needed to run this protocol. The appropriate template for doing so is provided in the input_csv.csv in this repository (see the Normalization-with-csv/ directory). Do not change the column names in the first row of this file. Also do not add 0 before single-digit numbers of well locations (i.e. put "A1" and do not put "A01")

2. Open the Jupyter Notebook file (Generate_dictionaries_for_pooling-240208.ipynb) and follow the instructions. You do this first by starting jupyter notebook first, then opening the file. To start jupyter notebook, open the terminal and type "jupyter notebook" and press enter. You can then open .ipynb files within the juper notebook interface. When complete, copy the information at the very bottom. This is to be pasted into the OT-2 protocol python file. 

  **Example copy/paste output of the Jupyter Notebook file generated from the input_csv.csv provided:**

    source_well_to_destination_well_dictionary = {'A1': 'B1', 'B2': 'C2', 'C3': 'D3', 'D4': 'E4', 'E5': 'F5'}
    water_addition_dictionary =  {'B1': '0', 'C2': '5', 'D3': '10', 'E4': '24', 'F5': '26'}
    DNA_addition_dictionary =  {'A1': '26', 'B2': '21', 'C3': '16', 'D4': '2', 'E5': '0'}

3. Paste the information into the "PASTE HERE" section in the OT-2 Python protocol file.

4. SAVE AS. Best practice is to add a date and your initials to the new file's name (e.g. normalization-with-csv-240208-blm.py).

5. Import this file to the OpenTrons Software.

6. Run labware check to calibrate the machine. THIS IS IMPORTANT-- on the DNA plate (where the DNA is in micronics tubes), which is in slot 3, the machine thinks it is a biorad 96 well plate. The calibration that works the best with getting all the sample out of the tubes especially if the volume is less than 50ul, is to calibrate the pipette 2.5mm lower than recommended at this step. I include a screenshot of the calibration parameters in this repo for your reference, too.

8. Start run! :)
