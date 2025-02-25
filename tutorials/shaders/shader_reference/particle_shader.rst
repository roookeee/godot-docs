.. _doc_particle_shader:

Particle shaders
================

Particle shaders are a special type of vertex shader that runs before the
object is drawn. They are used for calculating material properties such as
color, position, and rotation. They are drawn with any regular material for
CanvasItem or Spatial, depending on whether they are 2D or 3D.

Particle shaders are unique because they are not used to draw the object
itself; they are used to calculate particle properties, which are then used
by the CanvasItem of Spatial shader. They contain only a vertex processor
function that outputs multiple properties (see built-ins below).

Particle shaders use a transform feedback shader, which is a special type of
vertex shader that runs on its own. It takes in data in a buffer like a regular
vertex shader does, but it also outputs to data buffers instead of outputting
to the fragment shader for pixel-processing. Because of this, transform feedback
shaders can build on themselves each run, unlike other shaders that discard the
data they have calculated once they draw to the frame buffer.

.. note:: Particle shaders are only available in the GLES3 backend. If you need
          particles in GLES2, use :ref:`CPUParticles3D <class_CPUParticles3D>`.

Render modes
^^^^^^^^^^^^

+-----------------------+----------------------------------------+
| Render mode           | Description                            |
+=======================+========================================+
| **keep_data**         | Do not clear previous data on restart. |
+-----------------------+----------------------------------------+
| **disable_force**     | Disable attractor force.               |
+-----------------------+----------------------------------------+
| **disable_velocity**  | Ignore **VELOCITY** value.             |
+-----------------------+----------------------------------------+

Built-ins
^^^^^^^^^

Values marked as "in" are read-only. Values marked as "out" are for optional writing and will
not necessarily contain sensible values. Values marked as "inout" provide a sensible default
value, and can optionally be written to. Samplers are not subjects of writing and they are
not marked.

Global built-ins
^^^^^^^^^^^^^^^^

Global built-ins are available everywhere, including custom functions.

+-------------------+----------------------------------------------------------------------------------------+
| Built-in          | Description                                                                            |
+===================+========================================================================================+
| in float **TIME** | Global time, in seconds.                                                               |
+-------------------+----------------------------------------------------------------------------------------+
| in float **PI**   | A ``PI`` constant (``3.141592``).                                                      |
|                   | A ration of circle's circumference to its diameter and amount of radians in half turn. |
+-------------------+----------------------------------------------------------------------------------------+
| in float **TAU**  | A ``TAU`` constant (``6.283185``).                                                     |
|                   | An equivalent of ``PI * 2`` and amount of radians in full turn.                        |
+-------------------+----------------------------------------------------------------------------------------+
| in float **E**    | A ``E`` constant (``2.718281``). Euler's number and a base of the natural logarithm.   |
+-------------------+----------------------------------------------------------------------------------------+

Start and Process built-ins
^^^^^^^^^^^^^^^^^^^^^^^^^^^

+---------------------------------+--------------------------------------------------------------------------------+
| Function                        | Description                                                                    |
+=================================+================================================================================+
| in float **LIFETIME**           | Particle lifetime.                                                             |
+---------------------------------+--------------------------------------------------------------------------------+
| in float **DELTA**              | Delta process time.                                                            |
+---------------------------------+--------------------------------------------------------------------------------+
| in uint **NUMBER**              | Unique number since emission start.                                            |
+---------------------------------+--------------------------------------------------------------------------------+
| in uint **INDEX**               | Particle index (from total particles).                                         |
+---------------------------------+--------------------------------------------------------------------------------+
| in mat4 **EMISSION_TRANSFORM**  | Emitter transform (used for non-local systems).                                |
+---------------------------------+--------------------------------------------------------------------------------+
| in uint **RANDOM_SEED**         | Random seed used as base for random.                                           |
+---------------------------------+--------------------------------------------------------------------------------+
| inout bool **ACTIVE**           | ``true`` when Particle is active, can be set ``false``.                        |
+---------------------------------+--------------------------------------------------------------------------------+
| inout vec4 **COLOR**            | Particle color, can be written to and accessed in mesh's vertex function.      |
+---------------------------------+--------------------------------------------------------------------------------+
| inout vec3 **VELOCITY**         | Particle velocity, can be modified.                                            |
+---------------------------------+--------------------------------------------------------------------------------+
| inout mat4 **TRANSFORM**        | Particle transform.                                                            |
+---------------------------------+--------------------------------------------------------------------------------+
| inout vec4 **CUSTOM**           | Custom particle data. Accessible from shader of mesh as **INSTANCE_CUSTOM**.   |
+---------------------------------+--------------------------------------------------------------------------------+
| inout float **MASS**            | Particle mass, intended to be used with attractors. Equals ``1.0`` by default. |
+---------------------------------+--------------------------------------------------------------------------------+

.. note:: In order to use the ``COLOR`` variable in a StandardMaterial3D, set ``vertex_color_use_as_albedo``
          to ``true``. In a ShaderMaterial, access it with the ``COLOR`` variable.

Start built-ins
^^^^^^^^^^^^^^^

+---------------------------------+-------------+
| Built-in                        | Description |
+=================================+=============+
| in bool **RESTART_POSITION**    |             |
+---------------------------------+-------------+
| in bool **RESTART_ROT_SCALE**   |             |
+---------------------------------+-------------+
| in bool **RESTART_VELOCITY**    |             |
+---------------------------------+-------------+
| in bool **RESTART_COLOR**       |             |
+---------------------------------+-------------+
| in bool **RESTART_CUSTOM**      |             |
+---------------------------------+-------------+
| in bool **RESTART_VELOCITY**    |             |
+---------------------------------+-------------+

Process built-ins
^^^^^^^^^^^^^^^^^

+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| Built-in                           | Description                                                                                                                             |
+====================================+=========================================================================================================================================+
| in bool **RESTART**                | ``true`` if the current process frame is first for the particle.                                                                        |
+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| in uint **FLAG_EMIT_POSITION**     | A flag for using on the last argument of ``emit_subparticle`` function to assign a position to a new particle's transform.              |
+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| in uint **FLAG_EMIT_ROT_SCALE**    | A flag for using on the last argument of ``emit_subparticle`` function to assign the rotation and scale to a new particle's transform.  |
+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| in uint **FLAG_EMIT_VELOCITY**     | A flag for using on the last argument of ``emit_subparticle`` function to assign a velocity to a new particle.                          |
+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| in uint **FLAG_EMIT_COLOR**        | A flag for using on the last argument of ``emit_subparticle`` function to assign a color to a new particle.                             |
+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| in uint **FLAG_EMIT_CUSTOM**       | A flag for using on the last argument of ``emit_subparticle`` function to assign a custom data vector to a new particle.                |
+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| in bool **COLLIDED**               | ``true`` when the particle has collided with a particle collider.                                                                       |
+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| in vec3 **COLLISION_NORMAL**       | A normal of the last collision. If there is no collision detected it is equal to ``vec3(0.0)``.                                         |
+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| in float **COLLISION_DEPTH**       | A length of normal of the last collision. If there is no collision detected it is equal to ``0.0``.                                     |
+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| in vec3 **ATTRACTOR_FORCE**        | A combined force of the attractors at the moment on that particle.                                                                      |
+------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

Process functions
^^^^^^^^^^^^^^^^^

+--------------------------------------------------------------------------------------------+-----------------------------------------------+
| Function                                                                                   | Description                                   |
+============================================================================================+===============================================+
| bool **emit_subparticle** (mat4 xform, vec3 velocity, vec4 color, vec4 custom, uint flags) | Forces to emit a particle from a sub-emitter. |
+--------------------------------------------------------------------------------------------+-----------------------------------------------+
