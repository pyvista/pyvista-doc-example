Using PyVista with Jupyter Execute
==================================

.. note::
   Be sure to read the main documentation page `PyVista - Jupyter
   Notebook Plotting <https://docs.pyvista.org/user-guide/jupyter/index.html>`_
   for more details about using PyVista with JupyterLab.

PyVista also supports the `jupyter-sphinx
<https://jupyter-sphinx.readthedocs.io/>`_ extension. With this extension you
can execute code blocks within a sphinx ``*.rst`` file using the
``jupyter-execute`` directive::

  .. jupyter-execute::

     name = 'world'
     print('hello ' + name + '!')

Will be rendered as:

.. jupyter-execute::

   name = 'world'
   print('hello ' + name + '!')

|

Likewise, output from PyVista that would normally be rendered within a notebook
will be rendered in the output cell from the ``jupyter-execute`` directive. For
example, here's a plot using the `panel <https://github.com/holoviz/panel>`_
backend::

  .. jupyter-execute::

     from pyvista import examples
     dataset = examples.download_urn()
     dataset.plot(
         color='tan',
         jupyter_backend='panel',
         smooth_shading=True,
         window_size=[600, 400]
     )

Which is rendered as:

.. jupyter-execute::

   from pyvista import examples
   dataset = examples.download_urn()
   dataset.plot(
       color='tan',
       jupyter_backend='panel',
       smooth_shading=True,
       window_size=[600, 400]
   )


Using the ``Panel`` backend with PyVista
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
PyVista supports the usage of the `panel <https://github.com/holoviz/panel>`_
library as a ``vtk.js`` jupyterlab plotting backend that can be utilized as
either a standalone VTK viewer, or as a tightly integrated ``pyvista`` plotting
backend.  For example, within a Jupyter notebook environment, you can pass
``jupyter_backend='panel'`` to ``plot``, or ``Plotter.show`` to automatically
enable plotting with Juptyer and ``panel``.

For example, here's the ``PyVista`` logo::

   .. jupyter-execute::

      from pyvista import demos
      demos.plot_logo(background='white', jupyter_backend='panel')

Which is shown within the documentation as:

.. jupyter-execute::

   from pyvista import demos
   demos.plot_logo(background='white', jupyter_backend='panel')

|

Examples and Usage
~~~~~~~~~~~~~~~~~~
There are two ways to use `panel <https://github.com/holoviz/panel>`_ within
Jupyter notebooks.  You can use it on a plot by plot basis by setting the
``jupyter_backend`` in ``mesh.plot()``::

   .. jupyter-execute::

       import pyvista as pv
       from pyvista import examples

       # create a point cloud from lidar data and add height scalars
       dataset = examples.download_lidar()
       point_cloud = pv.PolyData(dataset.points[::100])
       point_cloud['height'] = point_cloud.points[:, 2]
       point_cloud.plot(window_size=[500, 500],
                        jupyter_backend='panel',
                        cmap='jet',
                        point_size=2,
                        background='w')

And here's the resulting output in Sphinx:

.. jupyter-execute::

    import pyvista as pv
    from pyvista import examples

    # create a point cloud from lidar data and add height scalars
    dataset = examples.download_lidar()
    point_cloud = pv.PolyData(dataset.points[::100])
    point_cloud['height'] = point_cloud.points[:, 2]
    point_cloud.plot(window_size=[500, 500],
                     jupyter_backend='panel',
                     cmap='jet',
                     point_size=2,
                     background='w')

|

Or you can first hide code that sets up the plotting backend and global theme::

   .. jupyter-execute::
       :hide-code:

       import pyvista as pv

       # Set the global jupyterlab backend.  All plots from this point
       # onward will use the ``panel`` backend and do not have to be
       # specified in ``show``
       pv.set_jupyter_backend('panel')
       pv.global_theme.background = 'white'
       pv.global_theme.axes.show = False
       pv.global_theme.smooth_shading = True
       pv.global_theme.antialiasing = True

.. jupyter-execute::
   :hide-code:

   import pyvista as pv
   pv.set_jupyter_backend('panel')
   pv.global_theme.background = 'white'
   pv.global_theme.axes.show = False
   pv.global_theme.smooth_shading = True
   pv.global_theme.antialiasing = True


And now just directly execute ``plot`` on any dataset::

   .. jupyter-execute::

      from pyvista import examples
      dataset = examples.download_dragon()
      dataset.plot(cpos="xy", scalars=dataset.points[:, 2], cmap='bwr')

Which looks like:

.. jupyter-execute::

   from pyvista import examples
   dataset = examples.download_dragon()
   dataset.plot(cpos="xy", scalars=dataset.points[:, 2], cmap='bwr')


.. note::
   You have the option of choosing `panel <https://github.com/holoviz/panel>`_
   or `pythreejs <https://github.com/jupyter-widgets/pythreejs>`_ as a backend,
   but you might find that `panel <https://github.com/holoviz/panel>`_ has
   better support as it's being actively developed.
