.. augmentdata documentation master file, created by
   sphinx-quickstart on Fri May  1 14:54:11 2020.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to the documentation of KNNOR - a novel data augmentation technique!
=======================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:



KNNOR
===========

Generic python library to perform augmentation of data



Features
--------

- Help balance datasets by upsampling
- Enhance accuracy of models

Installation
------------

Install knnor by running::
   pip install knnor

Using the Library
-----------------

Convert your dataset to numpy array

All values of the data must be numeric

Separate the data into X and y

X being the feataures and y being the class labels



.. code-block:: python

  import numpy as np
  from knnor import data_augment
  l=[

    [1.0,2.0,1.0,0],
    [1,3,1,0],
    [2,1,1,0],
    [3,2,1,0],
    [3,1,1,0],

    [1,3,4,1],
    [1,4,3,1],
    [1,4,4,1],

    [2,3,3,1],
    [2,3,4,1],
    [2,4,3,1],
    [2,4,4,1],

    [3,2,2,1],
    [3,3,2,1],
    [3,3,2,1],
    [3,4,2,1],

    [4,3,1,1]
  ]

  l=np.array(l)
  print("Original Data:")
  print(l)
  X=l[:,:-1]
  y=l[:,-1]

  knnor = data_augment.KNNOR()
  knnor=KNNOR()
  X_new,y_new=knnor.fit_resample(X,y)
  y_new=y_new.reshape(-1,1)

  print("KNNOR Data:")
  new_data=np.append(X_new, y_new, axis=1)
  print(new_data)


   

new_data contains the augmented data

.. code-block:: python

  Original Data:
  [[1. 2. 1. 0.]
   [1. 3. 1. 0.]
   [2. 1. 1. 0.]
   [3. 2. 1. 0.]
   [3. 1. 1. 0.]
   [1. 3. 4. 1.]
   [1. 4. 3. 1.]
   [1. 4. 4. 1.]
   [2. 3. 3. 1.]
   [2. 3. 4. 1.]
   [2. 4. 3. 1.]
   [2. 4. 4. 1.]
   [3. 2. 2. 1.]
   [3. 3. 2. 1.]
   [3. 3. 2. 1.]
   [3. 4. 2. 1.]
   [4. 3. 1. 1.]]

  KNNOR Data:
  [[1.         2.         1.         0.        ]
   [1.         3.         1.         0.        ]
   [2.         1.         1.         0.        ]
   [3.         2.         1.         0.        ]
   [3.         1.         1.         0.        ]
   [1.         3.         4.         1.        ]
   [1.         4.         3.         1.        ]
   [1.         4.         4.         1.        ]
   [2.         3.         3.         1.        ]
   [2.         3.         4.         1.        ]
   [2.         4.         3.         1.        ]
   [2.         4.         4.         1.        ]
   [3.         2.         2.         1.        ]
   [3.         3.         2.         1.        ]
   [3.         3.         2.         1.        ]
   [3.         4.         2.         1.        ]
   [4.         3.         1.         1.        ]
   [1.         2.8596414  1.         0.        ]
   [3.         1.89795961 1.         0.        ]
   [2.76031358 1.         1.         0.        ]
   [1.         2.95194388 1.         0.        ]
   [3.         1.72737314 1.         0.        ]
   [2.712059   1.         1.         0.        ]
   [1.         2.94970565 1.         0.        ]]


Input Parameters
----------------

Above example leverages the default parameters of the KNNOR algorithm. Following parameters can be used to tweak the functioning of the algorithm

.. code-block:: python
  X_new,y_new,_,_=knnor.fit_resample(X,y,
                              num_neighbors=10, # the number of neighbors that will be used for generation of each artificial point
                              max_dist_point=0.01, # the maximum distance at which the new point will be placed
                              proportion_minority=0.3, # proportion of the minority population that will be used to generate the artificial point
                              final_proportion=2 # final number of minority datapoints
                               # example, if num majority =15 and num minority =5, 
  #           putting final_proportion as 1 will add 10 artificial minority points
                              )


- num_neighbors is the number of neighbors that will be used for generation of each artificial point
- max_dist_point is the maximum distance at which the new point will be placed, 1 being highest
- proportion_minority is the proportion of the minority population that will be used to generate the artificial point
- final_proportion decides the number of minority datapoints to be augmented. For example, if the number of majority datapoints is 15 and the number of minority datapoints is 5, then final_proportion=1 implies that 10 artificial minority points will be added so that the ratio of minority over majority count is 1.




Outputs
-------
- X: complete data with augmented datapoints

- y: Labels including the augmented ones


.. Contribute
.. ----------

.. - Issue Tracker: github.com/$project/$project/issues
.. - Source Code: github.com/$project/$project

Support
-------

If you are having issues, please let us know at
ashhadulislam@gmail.com or samir.brahim@gmail.com

Cite
-------
If you are using this library in your research please cite the following.

Ashhadul Islam, Samir Brahim Belhaouari, Atiq Ur Rahman, Halima Bensmail,
KNNOR: An oversampling technique for imbalanced datasets,
Applied Soft Computing,
2021,
108288,
ISSN 1568-4946,
https://doi.org/10.1016/j.asoc.2021.108288.

(https://www.sciencedirect.com/science/article/pii/S1568494621010942)



License
-------

The project is licensed under the MIT license.

Code
-------

The code can be found in github: 

https://github.com/ashhadulislam/augmentdatalib_source

More examples can be found at 

https://github.com/ashhadulislam/augmentdatalib_source/blob/master/example/Example.ipynb