# HCP-reproducibility-paper
A repository for the HCP reproducibility paper

## How to contribute

Fork the repository, edit ```paper.tex``` and other files directly, and make a pull-request. 

Add your name and affiliation to the list of co-authors. Contact
tristan.glatard@concordia.ca if you feel that the list or order of
authors should be amended.

## How to add comments

Use command ```\note``` in ```paper.tex``` as follows: ```\note{John}{This is a comment}```.

## How to generate the figures

### Fig 1

* `python ./bin/code/provenance_graph.py`

### Fig. 3
* `python ./bin/code/heatmap_plot.py`

### Fig. 4

* [Source files](Consider:/data/asalari/ali-tests/paper_images/pfs_fnirt_imgs/)

### Fig. 5

1. Create binarized difference images of each subject:
    ```
    mri_convert aseg.hires_1-1.mgz aseg.hires_1-1.nii.gz
    fslmaths aseg.hires_1-1.nii.gz -sub aseg.hires_1-2.nii.gz diff1.nii.gz
    fslmaths diff1.nii.gz -bin diff_bin1.nii.gz
    ```

2. From a terminal, run:

    ```
    python ./bin/code/binarized_heatmap_img.py input_folder_of_bin_imgs ./bin/figs/binarized.png reference_img.nii.gz
    ```

Note: All the subject images, binarized images and reference image that we used are available in [link](Consider:/data/asalari/ali-tests/paper_images/fs_aseg_imgs) 

### Fig. 6

1. Compute dice value of difference images of each subject in a .csv file:
    ```
    python ./bin/code/Dice_region_csv.py first_img.nii.gz second_img.nii.gz fs_seg_dice_accumulated_20sbj.csv
    ``` 
Note: All the images are available in [link](Consider:/data/asalari/ali-tests/paper_images/fs_aseg_imgs)

2. * `python bin/code/regions.py`

## How to generate the pdf

(You may edit ```paper.tex``` without generating the pdf if you don't manage to).

0. Install ```pdflatex``` and ```bibtex```
1. Compile the document: ```pdflatex paper ; pdflatex paper``` (yes, twice).
2. Generate the bibliography: ```bibtex paper ; pdflatex paper``` (yes, once again).

