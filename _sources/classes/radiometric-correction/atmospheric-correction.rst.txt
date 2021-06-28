Atmospheric Correction
++++++++++++++++++++++


Read Recommendation
"""""""""""""""""""


- :ref:`Gaida et al. (2020) - Correção Atmosférica em Sensoriamento Remoto: Uma Revisão <Gaida2020>`.


- `A First Course in Atmospheric Radiation <https://www.amazon.com.br/First-Course-Atmospheric-Radiation/dp/0972903313>`_


Atmospheric Correction
""""""""""""""""""""""


Atmospheric correction is the process of removing, or reducing the effects of the atmosphere constituents that affects the radiance measured by an imaging system, to produce surface reflectance values. Atmospheric correction can improve the interpretability and use of an image. However, the efficacy of the atmosphere correction procedure depends on the correction method, which ideally, requires knowledge of the atmospheric conditions and aerosol properties at the time the image was acquired. There are two categories of atmospheric correction approaches: (1) relative normalization (Schroeder et al., 2006) and absolute correction (Chávez, 1996; Song and Woodcock, 2003).


Relative normalization involves adjusting the radiometry to a reference image based on the relationship between pseudo-invariant features from multi-date images. Absolute correction can be further divided into two categories: empirical and physical-based approaches. Empirical methods are simple and use the spectral response of specific targes of the scene, e. g. water, to estimate atmospheric parameters. An advantage of this method is that it does not require external information of the atmospheric parameters. However they are less accurate than physical. The *Dark-Object Subtraction* (DOS) method is a widely used empirical method for estimating the path radiance based on the darkest value in the image (Song and Woodcock, 2003). DOS is relatively simple, but it does not consider the pixel-to-pixel variation in atmospheric effects. 


This method is used when there is no available data on atmospheric conditions and aerosol properties at the time the image was acquired. The basic assumption of this method is that within the image some pixels are in complete shadow and their radiances received at the satellite are due entirely to atmospheric scattering (path radiance). This path radiance value is then subtracting from each pixel value in the image. The accuracy of these techniques are generally lower than physically-based corrections, but they are useful when no atmospheric measurements are available.


The physical-based approaches, such as *Atmospheric/Topographic CORrection* (ATCOR; Richter, 1997), *MODerate resolution atmospheric TRANsmission* (MODTRAN; Berk et al., 1998), and the *Satellite Signal in the Solar Spectrum* (6S) code (Vermote et al., 1997), are able to consider the heterogeneity of the atmosphere, but need many complicated steps and manual operations, which make them difficult to process large amount of Landsat time series.


.. figure:: ./imgs/modtran-attenuation.png
    :alt: MODTRAN
    :width: 600
    :figclass: align-center
    :name: fig:modtran


    MODTRAN attenuation Sources. **Source** Alexander (Lex) GRSS presentation.


Atmospheric models can be used to account for the effects of scattering and absorption in the atmosphere. A number of parameters are required to accurately apply atmospheric correction, including properties such as the amount of water vapor, distribution of aerosols. Sometimes this data can be collected by field instruments that measure atmospheric gases and aerosols, but this is often expensive and time consuming. Other satellite data can also be used to help estimate the amount and distribution of atmospheric aerosols. Many software packages include special atmospheric correction modules that use atmospheric radiation transfer models to produce an estimate of the true surface reflectance. Nowadays there are several fully automated atmospheric correction methods, for instance the Landsat Ecosystem Disturbance Adaptive Processing System (LEDAPS) software (Masek et al.,2006), LaSRC, Sen2cor.


Atmospheric Correction Processor Dockers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


`LaSRC LEDAPS FMASK (all in one) <https://github.com/marujore/LaSRC-LEDAPS-Fmask>`_


`LaSRC <https://github.com/marujore/LaSRC-docker>`_


`Sen2cor <https://github.com/marujore/sen2cor>`_


References
""""""""""


.. _Gaida2020:

- GAIDA, W. BRUNIG, F. M., GALVÃO, L., PONZONI, F. Correção Atmosférica em Sensoriamento Remoto: Uma Revisão. Revista Brasileira de Geografia Física, volume 13. 2020. https://10.26848/rbgf.v13.1.p229-248.


.. _Zhu2017:

- Zhu, Z. Change detection using landsat time series: A review of frequencies, preprocessing, algorithms, and applications. ISPRS Journal of Photogrammetry and Remote Sensing, 130, 370–384. 2017. https://doi.org/10.1016/j.isprsjprs.2017.06.013.