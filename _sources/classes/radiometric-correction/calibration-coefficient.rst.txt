Calibration Coefficient
+++++++++++++++++++++++


The electromagnetic radiation intensity recorded by an imaging system for each pixel as a digital number (DN) can be converted to more real world units like radiance, reflectance or brightness temperature. However, the coefficients are sensor dependent requiring specific information in order to be used in the calibration process.


DN conversion to TOA Radiance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


The raw digital numbers (DN) in the images like Landsat can be converted to top-of-atmosphere (TOA) radiance. Equations adequate the sensor measured data using sensor-specific information.


.. math:: L_{\lambda} = M_{L}Q_{cal} + A_{L}


where:

:math:`L_{\lambda}` = TOA spectral radiance (:math:`Watts/(m^{2} * srad * \mu m)`);

:math:`M_{L}` = Band-specific multiplicative rescaling factor from the metadata;

:math:`A_{L}` = Band-specific additive rescaling factor from the metadata;

:math:`Q_{cal}` = Quantized and calibrated standard product pixel values (DN).


CBERS-4 coefficients: :ref:`Pinto et al., 2016 <Pinto2016>`;
Landsat-7 coefficients: `Landsat-7 User Guide <https://prd-wret.s3.us-west-2.amazonaws.com/assets/palladium/production/atoms/files/LSDS-1927_L7_Data_Users_Handbook-v2.pdf>`_


TOA Radiance conversion to TOA Reflectance
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Equations rescale the data based on sensor specific information and remove the effects of differences in illumination geometry (different solar angle, Earth-sun distance) by doing a ratio between the Radiantion leaving the Earth and the radiation reaching the Earth from the Sun.


.. math:: \frac{Radiance}{Irradiance}


.. math:: \rho_{p} = \frac{\pi * L_{\lambda}*d^{2}}{Esun_{\lambda}*cos(\theta_{s})}


where:

:math:`d` is the Earth Sun distance in astronomical unit;


:math:`Esun_{\lambda}'` is the solar exoatmospheric spectral irradiance;


:math:`cos(\theta_{s})` is the sun zenith = :math:`90^{\circ}` - sun elevation.


+-------------+----------+-------------+----------+
| d                                               +
+-------------+----------+-------------+----------+
| Day of Year | Distance | Day of Year | Distance |
+=============+==========+=============+==========+
| 1           | 0.98331  | 196         | 1.01646  |
+-------------+----------+-------------+----------+
| 15          | 0.98365  | 213         | 1.01497  |
+-------------+----------+-------------+----------+
| 32          | 0.98509  | 227         | 1.01281  |
+-------------+----------+-------------+----------+
| 46          | 0.98774  | 242         | 1.00969  |
+-------------+----------+-------------+----------+
| 60          | 0.99084  | 258         | 1.00566  |
+-------------+----------+-------------+----------+
| 74          | 0.99446  | 274         | 1.00119  |
+-------------+----------+-------------+----------+
| 91          | 0.99926  | 288         | 0.99718  |
+-------------+----------+-------------+----------+
| 106         | 1.00353  | 305         | 0.99253  |
+-------------+----------+-------------+----------+
| 121         | 1.00756  | 319         | 0.98916  |
+-------------+----------+-------------+----------+
| 135         | 1.01087  | 335         | 0.98608  |
+-------------+----------+-------------+----------+
| 152         | 1.01403  | 349         | 0.98426  |
+-------------+----------+-------------+----------+
| 166         | 1.01577  | 365         | 0.98331  |
+-------------+----------+-------------+----------+
| 182         | 1.01667  |             |          |
+-------------+----------+-------------+----------+


**Source**: `Landsat-7 User Guide <https://prd-wret.s3.us-west-2.amazonaws.com/assets/palladium/production/atoms/files/LSDS-1927_L7_Data_Users_Handbook-v2.pdf>`_


+-------------+----------------+--------------+--------------+-----------------+
| Landsat-7 :math:`Esun_{\lambda} (Watts/(m^{2} * \mu m))`                     |
+-------------+----------------+--------------+--------------+-----------------+
| Band Number | Landsat 7 ETM+ | Landsat 5 TM | Landsat 4 TM | Landsat 1-5 MSS |
+=============+================+==============+==============+=================+
| 1           | 1970           | 1958         | 1958         | 1848            |
+-------------+----------------+--------------+--------------+-----------------+
| 2           | 1842           | 1827         | 1826         | 1588            |
+-------------+----------------+--------------+--------------+-----------------+
| 3           | 1547           | 1551         | 1554         | 1235            |
+-------------+----------------+--------------+--------------+-----------------+
| 4           | 1044           | 1036         | 1033         | 856.6           |
+-------------+----------------+--------------+--------------+-----------------+
| 5           | 225.7          | 214.9        | 214.7        |                 |
+-------------+----------------+--------------+--------------+-----------------+
| 7           | 82.06          | 80.65        | 80.70        |                 |
+-------------+----------------+--------------+--------------+-----------------+
| 8           | 1369           |              |              |                 |
+-------------+----------------+--------------+--------------+-----------------+


**Source**: `Landsat-7 User Guide <https://prd-wret.s3.us-west-2.amazonaws.com/assets/palladium/production/atoms/files/LSDS-1927_L7_Data_Users_Handbook-v2.pdf>`_


**Source**: `Solar exoatmospheric spectral irradiances (ESUN) for the Landsat 1-7 data <https://www.usgs.gov/core-science-systems/nli/landsat/using-usgs-landsat-level-1-data-product>`_



+---------------------+-----------------------------------------------------------+------------------------------------------------------------+
| Spectral Bands (nm) + :math:`Esun_{\lambda}'` MUX :math:`Watts/(m^{2} * \mu m)` + :math:`Esun_{\lambda}'` AWFI :math:`Watts/(m^{2} * \mu m)` |
+=====================+===========================================================+============================================================+
| 450-520 (Blue)      + | 1958 :math:`\pm` 35                                     + 1952 :math:`\pm` 35                                        |
+---------------------+-----------------------------------------------------------+------------------------------------------------------------+
| 520-590 (Green)     + | 1852 :math:`\pm` 29                                     + 1852 :math:`\pm` 29                                        |
+---------------------+-----------------------------------------------------------+------------------------------------------------------------+
| 630-690 (Red)       + | 1559 :math:`\pm` 18                                     + 1545 :math:`\pm` 18                                        |
+---------------------+-----------------------------------------------------------+------------------------------------------------------------+
| 770-890 (NIR)       + | 1091 :math:`\pm` 11                                     + 1098 :math:`\pm` 11                                        |
+---------------------+-----------------------------------------------------------+------------------------------------------------------------+


**Source**: :ref:`Pinto et al., 2016 <Pinto2016>`


For more accurate reflectance calculations, per-pixel solar angles could be used instead of the scene center solar angle. While per-pixel solar zenith angles are not provided with the Landsat Level-1 products, tools are provided which allow users to create `angle bands <https://www.usgs.gov/land-resources/nli/landsat/solar-illumination-and-sensor-viewing-angle-coefficient-files>`_ .


NOTE: (For data prior to Landsat Collections processing) The recommended ESUN values Landsat 1-7 are listed in the table above. These values used with Landsat products currently generated at EROS ensure consistent radiometric calibration of data from all these sensors. (Note: although the data are consistently calibrated, calculated TOA reflectance over the same target may differ among the sensors due to the spectral bandpass difference.)


ESUN values are not required for Landsat 8 data because Landsat 8’s metadata file provides coefficients necessary to convert to radiance and reflectance from the quantized and calibrated DNs of the product.


`Relative Spectral Response (RSR) <https://landsat.usgs.gov/spectral-characteristics-viewer>`_ of the OLI spectral bands can be used along with the user’s preferred solar spectrum to calculate ESUN values corresponding to Landsat 8 OLI bands. ESUN values are derived from the ChKur spectrum. The ChKur spectrum is the combined Chance-Kurucz Solar Spectrum within MODTRAN 5 (2011, Berk, A., Anderson, G.P., Acharya, P.K., Shettler, E.P., `MODTRAN 5.2.0.0 User's Manual <http://instrumentation.tamu.edu/~ting/other/MODTRAN(R)5.2.0.0.doc>`_).


Conversion to Top of Atmosphere Brightness Temperature
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Thermal bands calibration is similar to the reflectance procedure. Data from many thermal sensors can be converted to Brightness Temperature, which is a temperature that is obtained by measure the emitted radiance of a surface, measured in Kelvin (K).


.. math:: T = \frac{K_{2}}{ln(\frac{K_{1}}{L_\lambda} + 1)}


where:

:math:`T` =  Top of atmosphere brightness temperature (K);

:math:`L_{\lambda}` = TOA spectral radiance (:math:`Watts/( m^{2} * srad * \mu m)`)

:math:`K_{1}` = Band-specific thermal conversion constant;

:math:`K_{2}` = Band-specific thermal conversion constant;


References
~~~~~~~~~~


.. _Pinto2016:

- PINTO, C., PONZONI, F., CASTRO, R., LEIGH, L., MISHRA, N., AARON, D., HELDER, D. FFirst in-Flight Radiometric Calibration of MUX and WFI on-Board CBERS-4. Remote Sensing. 2016. doi: http://10.3390/rs8050405.
