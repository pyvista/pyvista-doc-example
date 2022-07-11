PyVista Documentation Example
-----------------------------

This repository demonstrates how to use PyVista within Sphinx using both the
`sphinx-gallery <https://sphinx-gallery.github.io/>`_ and the PyVista plot
directive `pyvista-plot
<https://docs.pyvista.org/extras/plot_directive.html>`_.

Visit rendered documentation at: https://pyvista.github.io/pyvista-doc-example/

Getting Started
~~~~~~~~~~~~~~~
To get started, first clone this repository with::

  https://github.com/pyvista/pyvista-doc-example.git

Next, install the documentation build requirements with::

  pip install -r requirements_docs.txt


Build the Documentation
~~~~~~~~~~~~~~~~~~~~~~~

Finally, build the documentation locally with::

  make -C doc html

Or, if on Windows::

  cd doc
  make.bat

You will then find the generated documentation within the ``doc/_build``
directory. Open up ``index.html`` using your browser to see the documentation.
