

Background
=============

Energy systems modelling requires versatile tools to model systems with
different levels of accuracy and detail. In this regard a major part of
is the data handling including input collection, processing and result analysis.
There is yet no standardized or custom broadly used model-agnostic data container
in the scientific field of energy system modelling to hold energy system
related data. To enable transparency and reproducibility as well as reusability
of existing data, the following data model description has been developed to
store energy system related data in the datapackage format.

The Open Energy Modelling Framework (oemof) is a powefull tool for modelling
energy systems. The functionalties range from   large linear programming
market models to detailed MILP heating system or Battery models to asses
profitablilty of plants in current and future market environments. The undelying
concept and its generic implementation allows for a very versatile modelling.
Most oemof components are rather of an abstract type like for example
'LinearTransformer' which can be used to model different energy system components.

For building large energy system models, data is of often stored in tabular
data format (for example csv, databases, xlsx). Despite the powerful package,
instantiating oemof solph models from tabular data sources requires major
knowledge of the package and resources to build in/out data processing.


Facade concept
======================

To enbale for a standard input format so called Facade concept for oemof solph
component has been developed. Facades have multiple advantages:

* Allow to instantiate from two dimenisonal data sources
* Restricted, less generic mathematical representation leading to more
transparent modelling
* Allows to build a simple interface for for complex components that are
constructed on the basis of multiple oemof solph components.
* Facade can be mixed with oemof solph components in a model


Data model
=======================

The datamodel is extendable and could be applied for various frameworks
(PyPSA, calliope, etc.). However, currenty the implementation for reading
 datapackages is limited to oemof-tabular classifiers

Components and mathematical description
===============================



Pre- and postprocessing
========================

Temporal aggregation
-------------------------

TODO.

Standard output format
-------------------------

TODO.

Reproducible Workflows
=======================

Reproduciblility is a recurring point of discussions in the energy system
modelling community. Based on the presented software package we propose the
following workflow to build reproducible models.

The starting point of this workflow is the folder strucutre:

::

	|-- model
		|-- environment
			|--requirements.txt
		|-- raw-data
		|-- scenarios
			|--scenario1.toml
			|--scenatio2.toml
			|-- ...
		|-- scripts
			|--create_input_data.py
			|--compute.py
			|-- ...
		|-- results
			|--scenario1
				|--input
				|--output
			 |-- scenario2
				|--input
				|--ouput


The `raw-data` directory contains all input data files required to build the
input datapckages for your modelling. The `scenatios` directory allows you
to specify different scenarios and describe them in a basic way.  The scripts
inside the `scripts` directory will build input data for your scenarios from the
`.toml` files and the raw-data. In addition the script to compute the models
can be stored there.

Of course the structure may be adapted to your needs. However you should
provide all this data when publishing results.
