# Signal propagation tracking unveils Distinct Properties of Resting-State Network Dynamics

This repository includes the code required to reproduce the results in: "Signal propagation tracking unveils Distinct Properties of Resting-State Network Dynamics" Davide Momi*1, Zheng Wang*1, Sara Parmigiani2,3,4, Ezequiel Mikulan5, Sorenza P. Bastiaens1,6, Mohammad P. Oveisi1,7, Kevin Kadak1,6, Allison C. Waters8, Sean Hill1,9,10, Andrea Pigorini5, Corey J. Keller2,3,4, John D. Griffiths1, 9, 10

1 = Krembil Centre for Neuroinformatics, Centre for Addiction and Mental Health (CAMH),
Toronto
2 = Department of Psychiatry and Behavioral Sciences, Stanford University Medical Center, Stanford, California
3 = Veterans Affairs Palo Alto Healthcare System, and the Sierra Pacific Mental Illness, Research, Education, and Clinical Center, Palo Alto, California
4 = Wu Tsai Neuroscience Institute, Stanford, California
5 = Dipartimento di Scienze Biomediche e Cliniche "L.Sacco", Università degli Studi di Milano, Milano, Italy
6 = Institute of Medical Science, University of Toronto
7 = Institute of Biomedical Engineering, University of Toronto
8 = Nash Family Center for Advanced Circuit Therapeutics, Icahn School of Medicine at Mount Sinai, New York, NY, USA
9 = Department of Physiology, University of Toronto
10 = Department of Psychiatry, University of Toronto

#### Please read our paper, and if you use this code, please cite our paper:
wait for it

## Methodology, and general conceptual framework of the present work
(A) Single Pulse Electrical Stimulation (SPES) applied to an intracortical target region generates an early response (evoked potential waveform component) at scalp high-density electroencephalography (hd-EEG) channels sensitive to that region and its immediate neighbors (red arrows). This also appears in more distal connected regions after a short delay due to axonal conduction and polysynaptic transmission. Subsequently, second and sometimes third late evoked components are frequently observed (blue arrows). By identifying the stimulated network, we aim to untangle the extent to which this second component relies on intrinsic network activity versus recurrent whole-brain feedback activity. (B) A schematic of the spatial relationships of canonical resting-state networks (RSNs) as demonstrated in (ref). This hierarchy spans from separate unimodal regions distinguished by functional segregation to high-order transmodal regions characterized by integrative processes (ref). (C) Our aim was to investigate the nature of each evoked response and understand how they varied depending on the perturbed network. Specifically, we seek to distinguish the extent to which a response is influenced by the internal dynamics of the stimulated network versus its dependence on multimodal connections. In order to answer this question, precisely communication interruptions or ‘virtual lesions’ are introduced into an accurately fitting individual subject computational model of stimulus-evoked responses, and the resulting changes in the propagation pattern are evaluated. We anticipate that propagation dynamics will remain relatively stable when the stimulus is applied to a low-order unimodal network, suggesting that the measured empirical activity is predominantly internally generated. Conversely, for high-order multimodal networks, we hypothesize a suppression of late responses, indicative of their significant reliance on functional integration processes.


![alt text](https://github.com/Davi1990/Momi_et_al_2024/blob/main/Figure_1.png)


## Methodological workflow for characterizing the stimulated network and performing subject-specific connectome-based neurophysiological modeling of evoked potentials. 

(A) Simultaneous stereotactic electroencephalography (sEEG) and scalp high-density electroencephalography (hd-EEG) signals were recorded. The black triangle and dashed vertical line indicate the time at which SPES was delivered. For further details on the methodology and data preprocessing please refer to Parmigiani et al., 2022 (B) To pinpoint the brain network where the stimulus was delivered, we employed The Schaefer's atlas (Schaefer et al., 2018), which divides the brain into 1000 regions across seven distinct RSNs: visual, somatosensory, limbic, dorsal attention, ventral attention, frontoparietal and default mode. We then mapped this atlas to the individual's FreeSurfer parcellation. Subsequently, we identified the parcellation region that overlapped with the intracranial electrode responsible for delivering the stimulus, ultimately enabling us to determine the stimulated network. (C) To model-individual stimulus-evoked timeseries, the Jansen-Rit model (Jansen and Rit, 1995), a neural mass model comprising pyramidal, excitatory interneuron, and inhibitory interneuron populations was embedded in every parcel of the 200-parcel Schaefer atlas (Schaefer et al., 2018) for simulating and fitting neural activity time series. The connectivity between parcel was model using the diffusion-weighted MRI (DW-MRI) tractography computed from a sample of healthy young individuals from the Human Connectome Project (HCP) Dataset (Van Essen et al., 2012), and then averaged to give a grand-mean anatomical connectome. The SPES-induced depolarization of the resting membrane potential was modeled by a perturbing voltage offset to the mean membrane potential of the excitatory interneuron population. Next, a lead field matrix was employed to project the time series from the parcels into channel space, resulting in the generation of simulated scap hd-EEG measurements. The quality of fit (loss) was quantified by calculating the cosine similarity between the simulated and empirical stimulus-evoked time series. Optimization of model parameters was accomplished by leveraging the autodiff-computed gradient (Rall, 1981) between the objective function and the model parameters, employing the ADAM algorithm (Kingma and Ba, 2017). Ultimately, the optimized model parameters were utilized to generate the fitted, simulated stimulus-evoked hd-EEG activity, and we present comparisons with the empirical data.

![alt text](https://github.com/Davi1990/Momi_et_al_2024/blob/main/Figure_2.png)


## Data   

The data used in this study were taken from an open dataset collected at the “Claudio Munari'' Epilepsy Surgery Center of Milan in Italy (https://doi.org/10.17605/OSF.IO/WSGZP), where simultaneous stereotactic electroencephalography (sEEG) and high-density scalp EEG (hd-EEG) was recorded following intracortical single pulse electrical stimulation on 36 patients (median age = 33 ± 8 years, 21 female). All subjects had a history of drug-resistant, focal epilepsy, and were candidates for surgical removal/ablation of the seizure onset zone (SOZ). For details regarding the data acquisition and the preprocessing steps please refer to the original papers (Mikulan et al., 2020, Parmigiani et al., 2022).


Mikulan, E., Russo, S., Parmigiani, S., Sarasso, S., Zauli, F. M., Rubino, A., Avanzini, P., Cattani, A., Sorrentino, A., Gibbs, S., Cardinale, F., Sartori, I., Nobili, L., Massimini, M., & Pigorini, A. (2020). Simultaneous human intracerebral stimulation and HD-EEG, ground-truth for source localization methods. Scientific Data, 7(1), Article 1. https://doi.org/10.1038/s41597-020-0467-x
Parmigiani, S., Mikulan, E., Russo, S., Sarasso, S., Zauli, F. M., Rubino, A., Cattani, A., Fecchio, M., Giampiccolo, D., Lanzone, J., D’Orio, P., Del Vecchio, M., Avanzini, P., Nobili, L., Sartori, I., Massimini, M., & Pigorini, A. (2022). Simultaneous stereo-EEG and high-density scalp EEG recordings to study the effects of intracerebral stimulation parameters. Brain Stimulation, 15(3), 664–675. https://doi.org/10.1016/j.brs.2022.04.007

## Notebooks

|   | Run | View |
| - | --- | ---- |
| Replicating Empirical Results | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Davi1990/Momi_et_al_2024/blob/main/Figure_1.ipynb) | [![View the notebook](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.jupyter.org/github/Davi1990/NMA_project/blob/master/cnn.ipynb?flush_cache=true) |

