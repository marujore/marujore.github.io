Nadir BRDF (Bidirectional Reflectance Distribution Function)-Adjusted Reflectance (NBAR)
----------------------------------------------------------------------------------------


The Bi-directional Reflectance Distribution Function (BRDF) models the anisotropic scattering effects of surfaces under different illumination and observation conditions. In simple terms, BRDF describes mathematically the changes in reflectance that we observe when an illuminated target is viewed from different angles. BRDF enables prediction of surface reflectance as a function of solar and viewing geometry. The BRDF is wavelength dependent and is determined by the structural and optical properties of the surface. These properties include shadowing, multiple scattering, transmission, reflection, and absorption and emission by surface elements. The BRDF parameters derived from the BRDF fitting can be inverted to predict what reflectance should be in a given sensor/solar geometry. This allows prediction of reflectance for nadir observations at a mean solar zenith angle to generate Nadir BRDF adjusted reflectance (NBAR) products.


.. figure:: ./imgs/sensor_spectral_info.png
    :alt: HLS
    :width: 600
    :figclass: align-center
    :name: fig:sensor_spectral_info


    Landsat Sentinel Spectral Information.


C-factor
++++++++

To adjust the view and illumination angles (BRDF) between different sensors, e. g. Landsat 8 and Sentinel-2, normalizing the BRDF effects is desirable. Retrieving the BRDF information directly from medium resolution optical remote sensing data is not feasible with the current temporal and angular distribution of the data. Instead, the BRDF information needs to be ingested as a priori :ref:`(Claverie et al., 2018) <Claverie2018>`.


In this context, the c-factor technique :ref:`(Roy et al., 2018) <Roy2016>` uses fixed BRDF coefficients for each spectral band, i.e., a constant BRDF shape, derived from a large number of pixels in the MODIS 500m BRDF product (MCD43) that are globally and temporally distributed (> 15 billion pixels) :ref:`(Claverie et al., 2018) <Claverie2018>`.


.. math:: BRF(\theta_{s}, \theta_{v}, \phi, \lambda) = f_{iso}(\lambda) + f_{vol}(\lambda)K_{vol}(\theta_{s}, \theta_{v}, \phi, \lambda) + f_{geo}(\lambda)K_{geo}(\theta_{s}, \theta_{v}, \phi, \lambda)


where :math:`f_{iso}`, :math:`f_{vol}`, :math:`f_{geo}` are spectrally de- pendent BRDF model parameters;


:math:`K_{vol}` and :math:`K_{geo}` are the volumetric scattering and geometric-optical model kernels respectively which depend only on the sun-view geometry.


Bandpass
++++++++


Sensor harmonization may require adjustment of the differences between the spectral bands wavelenghts and width of different sensors. In HLS OLI spectral bandpasses are used as reference, to which the MSI spectral bands are adjusted by using a gain and offset for each band. HLS used *Earth Observing-1/Hyperion* to estimate the bandpass values :ref:`(Claverie et al., 2018) <Claverie2018>`.


Harmonized Landsat Sentinel (HLS)
+++++++++++++++++++++++++++++++++

.. figure:: ./imgs/HLS.png
    :alt: HLS
    :width: 600
    :figclass: align-center
    :name: fig:hls


    Harmonized Landsat Sentinel (HLS) processing. **Source** `HLS website <https://hls.gsfc.nasa.gov/algorithms/>`_.


https://hls.gsfc.nasa.gov/


Sensor Harmonization Processor
++++++++++++++++++++++++++++++


`Sentinel-2 Landsat-8 (UNDER DEVELOPMENT) <https://github.com/marujore/sensor_harmonization>`_


References
""""""""""


.. _Claverie2018:

- CLAVERIE, M. Ju, J., MASEK, J. G. DUNGAN, J. L., VERMOTE, E. F., ROGER, J. C., SKAKUN, S. V., JUSTICE, C. The Harmonized Landsat and Sentinel-2 surface reflectance data set. Remote Sensing of Environment, volume 219, p. 145--161. 2018. https://10.1016/j.rse.2018.09.002


.. _Roy2016:

- ROY, D. P., ZHANG, H. K., JU, J., GOMEZ-DANS, J. L., LEWIS, P. E., SCHAAF, C. B., SUN, Q., LI, J., HUANG, H., KOVALSKYY, V. A general method to normalize Landsat reflectance data to nadir BRDF adjusted reflectance. Remote Sensing of Environment, volume 176, p. 255--271. 2016. https://10.1016/j.rse.2016.01.023


.. _Wagener2015:

- WAGNER, F. H., BREDE, V., VERBESSELT, J. ARAGÃO, L. E. O. C. Correction of sun-sensor geometry effects from MODIS MCD43A1 product for tropical forest applications. proceedings Simpósio Brasileiro de Sensoriamento Remoto, volume 17, p. 1097--1104. 2015. http://www.dsr.inpe.br/sbsr2015/files/p0204.pdf.