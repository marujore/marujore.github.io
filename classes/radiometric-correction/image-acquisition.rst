Image acquisition and quantification
++++++++++++++++++++++++++++++++++++


Read Recommendation
"""""""""""""""""""


- Chapter 2.3 Image Sensing and Acquisition :ref:`Gonzales & Woods (2007) <gonzales_2007>`.
- Chapter 2.4 Image Sampling and Quantization :ref:`Gonzales & Woods (2007) <gonzales_2007>`.


Image acquisition and quantification
""""""""""""""""""""""""""""""""""""


When an imaging system measure a physical process generating a digital image, the image intensity values are proportional to the energy radiated by a physical source (e.g., electromagnetic waves) measured by the sensor. :numref:`Figure %s <fig:image-sensing>` shows the process in which electromagnetic waves (light) interacts with a scene element and is observed by an imaging system, projected into a plane and digitalized :ref:`Gonzales & Woods (2007) <gonzales_2007>`.


.. figure:: ./imgs/image-sensing.png
    :alt: Image Sensing
    :width: 600
    :figclass: align-center
    :name: fig:image-sensing

    An example of the digital image acquisition process. (a) Energy (“illumination”) source. (b) An element of a scene. (c) Imaging system. (d) Projection of the scene onto the image plane. (e) Digitized image. Source: :ref:`Gonzales & Woods (2007) <gonzales_2007>`.


A imagem system normally outputs continuous voltage waveform related to the amplitude and spatial behavior of the physical phenomenon being sensed. A digital image is created by converting the continuous sensed data, which involves two processes: *sampling* and *quantization*. Digitizing the coordinate values is called sampling. Digitizing the amplitude values is called quantization :ref:`Gonzales & Woods (2007) <gonzales_2007>`. This process is shown in :numref:`Figure %s <fig:quantization>`.


.. figure:: ./imgs/quantization.png
    :alt: Quantization
    :width: 600
    :figclass: align-center
    :name: fig:quantization


    Generating a digital image. (a) Continuous image. (b) A scan line from A to B in the continuous image, used to illustrate the concepts of sampling and quantization. (c) Sampling and quantization. (d) Digital scan line. Source: :ref:`Gonzales & Woods (2007) <gonzales_2007>`.


References
~~~~~~~~~~


.. _gonzales_2007:

- GONZALEZ, R. C.; WOODS, R. E. Digital image processing (3.ed.). Upper Saddle River, NJ, USA: Pearson, 2007. 976p. ISSN 1098-6596. ISBN 013168728X.
