.. augmentdata documentation master file, created by
   sphinx-quickstart on Fri May  1 14:54:11 2020.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to augmentdata's documentation!
=======================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:



augmentdata
===========

Generic python library to perform augmentation of data



Features
--------

- Help balance datasets by upsampling
- Enhance accuracy of models

Installation
------------

Install augmentdata by running::
   pip install augmentdata

Using the Library
-----------------

Convert your dataset to numpy array

All values of the data must be numeric

The last column must be the class label

.. code-block:: python

   import numpy as np
   from augmentdata import data_augment
   l=[
   [1,3,4,1],
   [2,3,4,1],
   [1,2,1,0],
   [3,2,1,0],
   [3,1,1,0],
   [2,1,1,0],
   [3,2,2,1],
   [3,4,2,1],
   [4,3,1,1]
   ]

   l=np.array(l)

   k=2
   randmx=1
   daug = data_augment.DataAugment()
   [Data_a,Ext_d,Ext_not]=daug.augment(data=l,k=k,class_ind=0,N=5,randmx=randmx)
   print(Data_a)

Data_a contains the augmented data

.. code-block:: python

   array([[1.        , 2.        , 1.        , 0.        ],
       [3.        , 2.        , 1.        , 0.        ],
       [3.        , 1.        , 1.        , 0.        ],
       [2.        , 1.        , 1.        , 0.        ],
       [1.29027148, 1.98510073, 1.        , 0.        ],
       [1.65549291, 1.4418645 , 1.        , 0.        ],
       [2.02559196, 1.01965248, 1.        , 0.        ],
       [2.79469135, 1.69371064, 1.        , 0.        ],
       [2.907707  , 1.38716444, 1.        , 0.        ],
       [1.        , 3.        , 4.        , 1.        ],
       [2.        , 3.        , 4.        , 1.        ],
       [3.        , 2.        , 2.        , 1.        ],
       [3.        , 4.        , 2.        , 1.        ],
       [4.        , 3.        , 1.        , 1.        ]])


Input Parameters
----------------

- data is the array like input of data, last column of data is class label	
- k is number of neighbors, it should be bigger or equal to 1
- class_ind is the value of data that needs to be augmented. For example, if the class labels are 0 or 1 and the datapoints for 0 need to be upsampled, class_ind=0
- N is the number of Datapoints that needs to be added
- randmx will be a value between 0 and 1, inclusive. smaller the randmx, closer is the data to each original data. randmx, uniform[0,randmx], ; randmx<=1




Outputs
-------
- Data_a: complete data with augmented datapoints

- Ext_d: Only the augmented data points

- Ext_not: The datapoints that was created but ignored

.. Contribute
.. ----------

.. - Issue Tracker: github.com/$project/$project/issues
.. - Source Code: github.com/$project/$project

Support
-------

If you are having issues, please let us know at
samir.brahim@gmail.com or ashhadulislam@gmail.com

License
-------

The project is licensed under the MIT license.