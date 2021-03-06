.. image:: https://badge.fury.io/py/labml.svg
    :target: https://badge.fury.io/py/labml
.. image:: https://pepy.tech/badge/labml
    :target: https://pepy.tech/project/labml

LabML
=====

LabML lets you monitor AI model training on mobile phones.

.. image:: https://raw.githubusercontent.com/vpj/lab/master/images/mobile.png
   :width: 50%
   :alt: Mobile view 

You can install this package using PIP.

.. code-block:: console

    pip install labml


To push to mobile website, you need obtain a token from `web.lab-ml.com <https://web.lab-ml.com>`_
(`Githup lab-ml/app <https://github.com/lab-ml/app/>`_), and save statistics with `tracker.save`.

PyTorch example
^^^^^^^^^^^^^^^

.. code-block:: python

    from labml import tracker, experiment
  
    with experiment.record(name='sample', exp_conf=conf, token: 'TOKEN from web.lab-ml.com'):
        for i in range(50):
            loss, accuracy = train()
            tracker.save(i, {'loss': loss, 'accuracy': accuracy})

TensorFlow 2.0 Keras example
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: python

    from labml import experiment
    from labml.utils.keras import LabMLKerasCallback
  
    with experiment.record(name='sample', exp_conf=conf, token: 'TOKEN from web.lab-ml.com'):
        for i in range(50):
            model.fit(x_train, y_train, epochs=conf['epochs'], validation_data=(x_test, y_test),
                      callbacks=[LabMLKerasCallback()], verbose=None)

You can read the guides about creating an  `experiment <http://lab-ml.com/guide/experiment.html>`_,
and saving statistics with `tracker <http://lab-ml.com/guide/tracker.html>`_ for details.

It automatically pushes data to Tensorboard, and you can keep your old experiments organized with the 
`LabML Dashboard <https://github.com/lab-ml/dashboard/>`_

.. image:: https://raw.githubusercontent.com/lab-ml/dashboard/master/images/screenshots/dashboard_table.png
   :width: 100%
   :alt: Dashboard Screenshot

All these software is open source,
and your logs will be stored locally for Tensorboard and `LabML Dashboard <https://github.com/lab-ml/dashboard/>`_.
You will only be sending data away for `web.lab-ml.com <https://web.lab-ml.com>`_ if you include a token url.
This can also be `locally installed <https://github.com/lab-ml/app/>`_.

LabML can also do a bunch of other things like keeping track of git commits,
handling `configurations, hyper-parameters <http://lab-ml.com/guide/configs.html>`_,
saving and loading `checkpoints <http://lab-ml.com/guide/experiment.html>`_,
and providing pretty logs.

.. image:: https://raw.githubusercontent.com/vpj/lab/master/images/logger_sample.png
   :width: 50%
   :alt: Logger output


Links
-----

`💬 Slack workspace for discussions <https://join.slack.com/t/labforml/shared_invite/zt-egj9zvq9-Dl3hhZqobexgT7aVKnD14g/>`_

`📗 Documentation <http://lab-ml.com/>`_

`📑 Articles & Tutorials <https://medium.com/@labml/>`_

`👨‍🏫 Samples <https://github.com/lab-ml/samples>`_


Citing LabML
------------

If you use LabML for academic research, please cite the library using the following BibTeX entry.

.. code-block:: bibtex

	@misc{labml,
	 author = {Varuna Jayasiri, Nipun Wijerathne},
	 title = {LabML: A library to organize machine learning experiments},
	 year = {2020},
	 url = {https://lab-ml.com/},
	}

