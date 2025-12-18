# ⚡️Data⚡️

⚡️ Set 1 - breast cancer
    5000 images for benign
    5000 images for malignant
    512 x 512 images, jpg
    high variance, seems work-able though
    
    this may be the best choice, because
    it will perform well with a well-trained CNN
    
    Primary task
        • Binary image classification: benign vs malignant

    Secondary tasks
        • Model calibration (probability reliability)
        • Feature attribution / saliency inspection

    Expected failure modes
        • Overfitting to stain color or scanner artifacts
        • Poor generalization to slides from unseen labs
    
⚡️ Set 2 - leukemia
    5000 images for beneign
    5000 images for early
    5000 images for pre
    5000 images for progressed
    512 x 512 images, jpg
    lots of blurry, dirty, artifact rich samples.
    i estimate this would train a poorly performing model
    
    Primary task
        • Multi-class classification: benign / early / pre / progressed

    Secondary tasks
        • Artifact-robust feature learning
        • Stage severity ordering (ordinal awareness)

    Expected failure modes
        • Model learning blur, dirt, or compression artifacts
        • Class confusion between adjacent disease stages
    
⚡️ Set 3 - blood cells
    ~2500 images for Lymphoblast
    ~3000 images for Lymphocyte
    ~2500 images for Myeloblast
    256 x 256 png images, they exist in 1200 x 1200
    high variance
    i estimate that it would be able to classify images
    from this data set. for example, if I split the data
    it would do well with predicting a myeloblast from this
    data set. unlikely to perform well for 'drawing the boxes
    YOLO style on a random sample from outside the data set'
    
    Primary task
        • Multi-class cell type classification
    Secondary tasks
        • In-distribution cell detection (centered objects)
        • Representation learning for morphology similarity
    Expected failure modes
        • Failure on non-centered or multi-cell images
        • Severe domain shift on external lab data
    
⚡️ Set 4 - electro-cardiograms
    978 samples with ekg reading and csv file
    images are 2200 x 1700 png
    csv have many readings for I, II, and III
    
    extremely well formatted, pre-processed data
    all the images line up, all the same markers in same places
    the ekg are hard to process due to signal overlaps
    this is kaggle competition with cash prize
    
    i estimate this as 90% a pre-processing job, identifying
    how likely certain pixels are to belong to which line...
    
    converting the pixels into signal should be straight foward
    
    Lead I
        LA − RA
        • Views the heart from the left side
        • Best for lateral wall activity
        • Normally upright P, QRS, T waves
        
    Lead II
        LL − RA
        • Views from the lower left
        • Aligns closely with the heart’s main electrical axis
        • Often the cleanest rhythm strip
        • Most commonly displayed continuously
        
    Lead III
        LL − LA
        • Views from the lower right
        • Complements Lead II
        • Useful for inferior wall assessment
        
    Primary task
        • Signal reconstruction: extract clean Lead I, II, III waveforms from images

    Secondary tasks
        • Beat segmentation (P, QRS, T detection)
        • Downstream rhythm classification

    Expected failure modes
        • Line overlap and lead crossing ambiguity
        • Non-continuous signal leading to categorical errors.
        
    
⚡️ Set 5 - bone marrow
    1000 of each type for training for BLA, EOS, LYT, MON, NGS, NIF, PMO
    200 of each type for testing for BLA, EOS, LYT, MON, NGS, NIF, PMO
    200 of each type for validation for BLA, EOS, LYT, MON, NGS, NIF, PMO
    
    there are some dupes and what looks like portions of sequences
    radical variation in the data set
    
    BLA = Blast cells
    EOS = Eosinophils
    LYT = Lymphocytes
    MON = Monocytes
    NGS = Neutrophilic granulocytes (segmented)
    NIF = Neutrophilic immature forms
    PMO = Promonocytes
    
    According to online knowlede, "bone marrow datasets are brutal,"
    so I expect this is going to perform poorly.
    
    Primary task
        • Multi-class cell lineage classification

    Secondary tasks
        • Lineage grouping (immature vs mature cells)
        • Confusion-aware uncertainty estimation

    Expected failure modes
        • Irreducible label noise from expert disagreement
        • Confusion between morphologically similar immature cells (PMO, NIF, BLA)
