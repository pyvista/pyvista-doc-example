PyVista Plot Directive
----------------------
You can generate static images of PyVista plots within sphinx using the
``pyvista-plot`` directive by adding the following to your ``conf.py``
when building your documentation using Sphinx.

.. code:: python

   extensions = [
       "sphinx.ext.napoleon",
       "pyvista.ext.plot_directive",
   ]

You can then issue the plotting directive within your sphinx
documentation files::

   .. pyvista-plot::
      :caption: A sphere
      :include-source: True

      >>> import pyvista
      >>> sphere = pyvista.Sphere()
      >>> out = sphere.plot()

Which will be rendered as:

.. pyvista-plot::
   :caption: This is a default sphere
   :include-source: True

   >>> import pyvista
   >>> sphere = pyvista.Sphere()
   >>> out = sphere.plot()

Use the directive with files
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can also use the ``pyvista-plot`` directive with files with::

   .. pyvista-plot:: plot.py

Which is rendered as:

.. pyvista-plot:: plot.py

If you wish, you can also specify which function you want from that file with::

   .. pyvista-plot:: plot.py plot_function1

Which is rendered as:

.. pyvista-plot:: plot.py plot_function1
