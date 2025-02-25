:github_url: hide

.. DO NOT EDIT THIS FILE!!!
.. Generated automatically from Godot engine sources.
.. Generator: https://github.com/godotengine/godot/tree/master/doc/tools/make_rst.py.
.. XML source: https://github.com/godotengine/godot/tree/master/modules/gltf/doc_classes/GLTFDocument.xml.

.. _class_GLTFDocument:

GLTFDocument
============

**Inherits:** :ref:`Resource<class_Resource>` **<** :ref:`RefCounted<class_RefCounted>` **<** :ref:`Object<class_Object>`

Description
-----------

Append a glTF2 3d format from a file, buffer or scene and then write to the filesystem, buffer or scene.

Properties
----------

+-------------------------------------------------------------+-----------------------------------------------------------+--------+
| :ref:`GLTFDocumentExtension[]<class_GLTFDocumentExtension>` | :ref:`extensions<class_GLTFDocument_property_extensions>` | ``[]`` |
+-------------------------------------------------------------+-----------------------------------------------------------+--------+

Methods
-------

+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| :ref:`Error<enum_@GlobalScope_Error>`         | :ref:`append_from_buffer<class_GLTFDocument_method_append_from_buffer>` **(** :ref:`PackedByteArray<class_PackedByteArray>` bytes, :ref:`String<class_String>` base_path, :ref:`GLTFState<class_GLTFState>` state, :ref:`int<class_int>` flags=0, :ref:`int<class_int>` bake_fps=30 **)** |
+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| :ref:`Error<enum_@GlobalScope_Error>`         | :ref:`append_from_file<class_GLTFDocument_method_append_from_file>` **(** :ref:`String<class_String>` path, :ref:`GLTFState<class_GLTFState>` state, :ref:`int<class_int>` flags=0, :ref:`int<class_int>` bake_fps=30, :ref:`String<class_String>` base_path="" **)**                     |
+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| :ref:`Error<enum_@GlobalScope_Error>`         | :ref:`append_from_scene<class_GLTFDocument_method_append_from_scene>` **(** :ref:`Node<class_Node>` node, :ref:`GLTFState<class_GLTFState>` state, :ref:`int<class_int>` flags=0, :ref:`int<class_int>` bake_fps=30 **)**                                                                 |
+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| :ref:`PackedByteArray<class_PackedByteArray>` | :ref:`generate_buffer<class_GLTFDocument_method_generate_buffer>` **(** :ref:`GLTFState<class_GLTFState>` state **)**                                                                                                                                                                     |
+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| :ref:`Node<class_Node>`                       | :ref:`generate_scene<class_GLTFDocument_method_generate_scene>` **(** :ref:`GLTFState<class_GLTFState>` state, :ref:`int<class_int>` bake_fps=30 **)**                                                                                                                                    |
+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| :ref:`Error<enum_@GlobalScope_Error>`         | :ref:`write_to_filesystem<class_GLTFDocument_method_write_to_filesystem>` **(** :ref:`GLTFState<class_GLTFState>` state, :ref:`String<class_String>` path **)**                                                                                                                           |
+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Property Descriptions
---------------------

.. _class_GLTFDocument_property_extensions:

- :ref:`GLTFDocumentExtension[]<class_GLTFDocumentExtension>` **extensions**

+-----------+-----------------------+
| *Default* | ``[]``                |
+-----------+-----------------------+
| *Setter*  | set_extensions(value) |
+-----------+-----------------------+
| *Getter*  | get_extensions()      |
+-----------+-----------------------+

.. container:: contribute

	There is currently no description for this property. Please help us by :ref:`contributing one <doc_updating_the_class_reference>`!

Method Descriptions
-------------------

.. _class_GLTFDocument_method_append_from_buffer:

- :ref:`Error<enum_@GlobalScope_Error>` **append_from_buffer** **(** :ref:`PackedByteArray<class_PackedByteArray>` bytes, :ref:`String<class_String>` base_path, :ref:`GLTFState<class_GLTFState>` state, :ref:`int<class_int>` flags=0, :ref:`int<class_int>` bake_fps=30 **)**

.. container:: contribute

	There is currently no description for this method. Please help us by :ref:`contributing one <doc_updating_the_class_reference>`!

----

.. _class_GLTFDocument_method_append_from_file:

- :ref:`Error<enum_@GlobalScope_Error>` **append_from_file** **(** :ref:`String<class_String>` path, :ref:`GLTFState<class_GLTFState>` state, :ref:`int<class_int>` flags=0, :ref:`int<class_int>` bake_fps=30, :ref:`String<class_String>` base_path="" **)**

.. container:: contribute

	There is currently no description for this method. Please help us by :ref:`contributing one <doc_updating_the_class_reference>`!

----

.. _class_GLTFDocument_method_append_from_scene:

- :ref:`Error<enum_@GlobalScope_Error>` **append_from_scene** **(** :ref:`Node<class_Node>` node, :ref:`GLTFState<class_GLTFState>` state, :ref:`int<class_int>` flags=0, :ref:`int<class_int>` bake_fps=30 **)**

.. container:: contribute

	There is currently no description for this method. Please help us by :ref:`contributing one <doc_updating_the_class_reference>`!

----

.. _class_GLTFDocument_method_generate_buffer:

- :ref:`PackedByteArray<class_PackedByteArray>` **generate_buffer** **(** :ref:`GLTFState<class_GLTFState>` state **)**

.. container:: contribute

	There is currently no description for this method. Please help us by :ref:`contributing one <doc_updating_the_class_reference>`!

----

.. _class_GLTFDocument_method_generate_scene:

- :ref:`Node<class_Node>` **generate_scene** **(** :ref:`GLTFState<class_GLTFState>` state, :ref:`int<class_int>` bake_fps=30 **)**

.. container:: contribute

	There is currently no description for this method. Please help us by :ref:`contributing one <doc_updating_the_class_reference>`!

----

.. _class_GLTFDocument_method_write_to_filesystem:

- :ref:`Error<enum_@GlobalScope_Error>` **write_to_filesystem** **(** :ref:`GLTFState<class_GLTFState>` state, :ref:`String<class_String>` path **)**

.. container:: contribute

	There is currently no description for this method. Please help us by :ref:`contributing one <doc_updating_the_class_reference>`!

.. |virtual| replace:: :abbr:`virtual (This method should typically be overridden by the user to have any effect.)`
.. |const| replace:: :abbr:`const (This method has no side effects. It doesn't modify any of the instance's member variables.)`
.. |vararg| replace:: :abbr:`vararg (This method accepts any number of arguments after the ones described here.)`
.. |constructor| replace:: :abbr:`constructor (This method is used to construct a type.)`
.. |static| replace:: :abbr:`static (This method doesn't need an instance to be called, so it can be called directly using the class name.)`
.. |operator| replace:: :abbr:`operator (This method describes a valid operator to use with this type as left-hand operand.)`
