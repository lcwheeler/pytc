================================
pytc documentation
================================
A python software package for analyzing Isothermal Titration Calorimetry data.
The name is a `portmanteau <https://xkcd.com/739/>`_ of Python and ITC.  

Introduction
============
`pytc <https://github.com/harmslab/pytc>`_ is python software used to extract
thermodynamic information from isothermal titration calorimetry (ITC)
experiments.  The program is a powerful and flexible tool for fitting
arbitrarily complex thermodynamic models to multiple ITC experiments
simultaneously.  We built it with three design principles:

 + **Open source and cross platform**. The full source code should be available.
   The program should not require proprietary software to run. 
 + **Ease of use**. Fitting basic models should be easy.  Implementing completely
   new thermodynamic models should be straightforward. 
 + **Accessible for users and programmers**.  It should have both a GUI and a 
   well-documented API. 

Our implementation is built on `python3 <https://www.python.org/>`_ extended with  `numpy <http://www.numpy.org/>`_ 
and `scipy <https://www.scipy.org/>`_.   The GUI is built on `pytq5 <http://pyqt.sourceforge.net/Docs/PyQt5/installation.html>`_ and `pandas <http://pandas.pydata.org/>`_.

Try it out!
===========

We have posted a `jupyter <https://jupyter.org/>`_ notebook demonstrating the
capabilities of the API on `binder <http://mybinder.org:/repo/harmslab/pytc-binder>`_.

.. image:: http://mybinder.org/badge.svg :target: http://mybinder.org:/repo/harmslab/pytc-binder

Features
========

 + Clean, pythonic API
 + Simple, cross-platform GUI based on `PyQt5 <https://riverbankcomputing.com/software/pyqt/intro>`_.
 + New models can be defined using a few lines of python code.
 + Easy integration with `jupyter <https://jupyter.org/>`_ notebooks for 
   writing custom fitting scripts.

Example code
============

Fit a :math:`Ca^{2+}/EDTA` binding experiment to a single-site binding model.

.. sourcecode:: python

    import pytc

    # Load in integrated heats from an ITC experiment
    e = pytc.ITCExperiment("demos/ca-edta/tris-01.DH",
                           pytc.indiv_models.SingleSite)

    # Create the global fitter, add the experiment, and fit
    g = pytc.GlobalFit()
    g.add_experiment(e)
    g.fit()

    # Print the results out
    g.plot()
    print(g.fit_as_csv)

GUI Screenshots
===============

SCREENSHOT HERE

Documentation
=============

 + `Installation <installation.html>`_
 + `Fitting models using the script API <http://mybinder.org:/repo/harmslab/pytc-binder>`_.
 + `Fitting models using the GUI API <LINK>`_.
 + `Description of individual experiment models included in package <indiv_models.html>`_.
 + `Description of global fits included in package <global_models.html>`_.
 + `Defining new models <writing_new_models.html>`_.

.. warning::
    **pytc** will fit all sorts of complicated models to your data. It is up to
    you to make sure the fit is justified by the data.  You should always 
    follow best practices for selecting the fit model.  To help with this, 
    **pytc** returns a residuals plot, the root-mean-squared error, the number
    of free parameters, and number of data points.  


     
.. toctree::
   :maxdepth: 2
   :caption: Contents:

   _api/pytc.rst

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`