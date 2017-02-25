.. highlight:: javascript
.. _project:

Project object
##############

``app.project``

**Description**

The project object represents an After Effects project. Attributes provide access to specific objects within the project, such as imported files or footage and compositions, and also to project settings such as the timecode base. Methods can import footage, create solids, compositions and folders, and save changes.

----

==========
Attributes
==========

.. _Project.activeItem:

Project.activeItem
*********************************************

``app.project.activeItem``

**Description**

The item that is currently active and is to be acted upon, or a null if no item is currently selected or if multiple items are selected.

**Type**

:ref:`Item` or null; read-only.

----

.. _Project.bitsPerChannel:

Project.bitsPerChannel
*********************************************

``app.project.bitsPerChannel``

**Description**

The color depth of the current project, either 8, 16, or 32 bits.

**Type**

Integer (8, 16, or 32 only); read/write.

----

.. _Project.displayStartFrame:

Project.displayStartFrame
*********************************************

``app.project.displayStartFrame``

**Description**

An alternate way of setting the Frame Count menu setting in the Project Settings dialog box to 0 or 1, and is equivalent to using the ``FramesCountType.FC_START_0`` or ``FramesCountType.FC_START_1`` enumerated values for the :ref:`framesCountType <project.framescounttype>`.

**Type**

Integer (0 or 1); read/write.

----

.. _Project.feetFramesFilmType:

Project.feetFramesFilmType
*********************************************

``app.project.feetFramesFilmType``

**Description**

The Use Feet + Frames menu setting in the Project Settings dialog box. Use this attribute instead of the old ``timecodeFilmType`` attribute.

**Type**

A ``FeetFramesFilmType`` enumerated value; read/write. One of:

-  ``FeetFramesFilmType.MM16``
-  ``FeetFramesFilmType.MM35``

----

.. _Project.file:

Project.file
*********************************************

``app.project.file``

**Description**

The ExtendScript File object for the file containing the project that is currently open.

**Type**

File object or null if project has not been saved; read-only.

----

.. _Project.footageTimecodeDisplayStartType:

Project.footageTimecodeDisplayStartType
*********************************************

``app.project.footageTimecodeDisplayStartType``

**Description**

The Footage Start Time setting in the Project Settings dialog box, which is enabled when Timecode is selected as the time display style.

**Type**

A ``FootageTimecodeDisplayStartType`` enumerated value; read/write. One of:

-  ``FootageTimecodeDisplayStartType.FTCS_START_0``
-  ``FootageTimecodeDisplayStartType.FTCS_USE_SOURCE_MEDIA``

----

.. _Project.framesCountType:

Project.framesCountType
*********************************************

``app.project.framesCountType``

**Description**

The Frame Count menu setting in the Project Settings dialog box.

**Type**

A ``FramesCountType`` enumerated value; read/write. One of:

-  ``FramesCountType.FC_START_1``
-  ``FramesCountType.FC_START_0``
-  ``FramesCountType.FC_TIMECODE_CONVERSION``

.. WARNING:: Setting this attribute to ``FramesCountType.FC_TIMECODE_CONVERSION`` resets the ``displayStartFrame`` attribute to 0.

----

.. _Project.framesUseFeetFrames:

Project.framesUseFeetFrames
*********************************************

``app.project.framesUseFeetFrames``

**Description**

The Use Feet + Frames setting in the Project Settings dialog box. True if using Feet + Frames; false if using Frames.

**Type**

Boolean; read/write.

----

.. _Project.gpuAccelType:

Project.gpuAccelType
*********************************************

``app.project.gpuAccelType``

.. note::
   This functionality was added in After Effects 13.8

**Description**

Get or set the current projects GPU Acceleration option.
see :ref:`app.availableGPUAccelTypes`

**Type**

A ``GpuAccelType`` enumerated value; read/write. One of:

- ``GpuAccelType.CUDA``
- ``GpuAccelType.Metal``
- ``GpuAccelType.OPENCL``
- ``GpuAccelType.SOFTWARE``

**Example**

The following sample code checks to see if there are queued items in the render queue, and if so queues them in AME but does not immediately start rendering::

    // access via scripting to Project Settings -> Video Rendering and Effects -> Use

    var currentGPUSettings = app.project.gpuAccelType; // returns the current value
    var type_str = "";

    // check the current value and alert the user

    switch(currentGPUSettings) {
        case GpuAccelType.CUDA:  type_str = "CUDA"; break;
        case GpuAccelType.METAL:    type_str = "Metal"; break;
        case GpuAccelType.OPENCL:       type_str = "OpenCL"; break;
        case GpuAccelType.SOFTWARE:     type_str = "Software"; break;
        default:    type_str = "UNKNOWN"; break;
        }

    alert("Your current setting is " + type_str);

    // set the value to Metal

    app.project.gpuAccelType = GpuAccelType.METAL;


----

.. _Project.items:

Project.items
*********************************************

``app.project.items``

**Description**

All of the items in the project.

**Type**

:ref:`ItemCollection`; read-only.

----

.. _Project.linearBlending:

Project.linearBlending
*********************************************

``app.project.linearBlending``

**Description**

True if linear blending should be used for this project; otherwise false.

**Type**

Boolean; read/write.

----

.. _Project.numItems:

Project.numItems
*********************************************

``app.project.numItems``

**Description**

The total number of items contained in the project, including folders and all types of footage.

**Type**

Integer; read-only.

**Example**

::

    n = app.project.numItems;
    alert("There are " + n + "items in this project.")

----

.. _Project.removeUnusedFootage:

Project.removeUnusedFootage()
*********************************************

``app.project.removeUnusedFootage()``

**Description**

Removes unused footage from the project. Same as the File > Remove Unused Footage command.

**Parameters**

None.

**Returns**

Integer; the total number of FootageItem objects removed.

----

.. _Project.renderQueue:

Project.renderQueue
*********************************************

``app.project.renderQueue``

**Description**

The renderqueue of the project.

**Type**

:ref:`RenderQueue`; read-only.

----

.. _Project.rootFolder:

Project.rootFolder
*********************************************

``app.project.rootFolder``

**Description**

The root folder containing the contents of the project; this is a virtual folder that contains all items in the Project panel, but not items contained inside other folders in the Project panel.

**Type**

:ref:`FolderItem`; read-only.

----

.. _Project.selection:

Project.selection
*********************************************

``app.project.selection``

**Description**

All items selected in the Project panel, in the sort order shown in the Project panel.

**Type**

Array of :ref:`Item objects <item>`; read-only.

----

.. _Project.timeDisplayType:

Project.timeDisplayType
*********************************************

``app.project.timeDisplayType``

**Description**

The time display style, corresponding to the Time Display Style section in the Project Settings dialog box.

**Type**

A ``TimeDisplayType`` enumerated value; read/write. One of:

-  ``TimeDisplayType.FRAMES``
-  ``TimeDisplayType.TIMECODE``

----

.. _Project.toolType:

Project.toolType
*********************************************

``app.project.toolType``

.. note::
    This functionality was added in After Effects 14.0

**Description**

Get and sets the active tool in the Tools panel.

**Type**

A ``ToolType`` enumerated value; read/write. One of:

- ``ToolType.Tool_Arrow``: Selection Tool
- ``ToolType.Tool_Rotate``: Rotation Tool
- ``ToolType.Tool_CameraMaya``: Unified Camera Tool
- ``ToolType.Tool_CameraOrbit``: Orbit Camera Tool
- ``ToolType.Tool_CameraTrackXY``: Track XY Camera Tool
- ``ToolType.Tool_CameraTrackZ``: Track Z Camera Tool
- ``ToolType.Tool_Paintbrush``: Brush Tool
- ``ToolType.Tool_CloneStamp``: Clone Stamp Tool
- ``ToolType.Tool_Eraser``: Eraser Tool
- ``ToolType.Tool_Hand``: Hand Tool
- ``ToolType.Tool_Magnify``: Zoom Tool
- ``ToolType.Tool_PanBehind``: Pan Behind (Anchor Point) Tool
- ``ToolType.Tool_Rect``: Rectangle Tool
- ``ToolType.Tool_RoundedRect``: Rounded Rectangle Tool
- ``ToolType.Tool_Oval``: Ellipse Tool
- ``ToolType.Tool_Polygon``: Polygon Tool
- ``ToolType.Tool_Star``: Star Tool
- ``ToolType.Tool_TextH``: Horizontal Type Tool
- ``ToolType.Tool_TextV``: Vertical Type Tool
- ``ToolType.Tool_Pen``: Pen Tool
- ``ToolType.Tool_Feather``: Mask Feather Tool
- ``ToolType.Tool_PenPlus``: Add Vertex Tool
- ``ToolType.Tool_PenMinus``: Delete Vertex Tool
- ``ToolType.Tool_PenConvert``: Convert Vertex Tool
- ``ToolType.Tool_Pin``: Puppet Pin Tool
- ``ToolType.Tool_PinStarch``: Puppet Starch Tool
- ``ToolType.Tool_PinDepth``: Puppet Overlap Tool
- ``ToolType.Tool_Quickselect``: Roto Brush Tool
- ``ToolType.Tool_Hairbrush``: Refine Edge Tool

**Examples**

The following sample code checks the current tool, and if it is not the Unified Camera Tool, sets the current tool to that::

    // Check the current tool, then set it to Unified Camera Tool (UCT).
    {
        // Assume a composition is selected in the project.
        var comp = app.project.activeItem;
        if (comp instanceof CompItem) {
            // Add a camera to the current comp. (Requirement for UCT.)
            var cameraLayer = comp.layers.addCamera("Test Camera", [comp.width/2, comp.height/2]);
            comp.openInViewer();

            // If the currently selected tool is not one of the camera tools, set it to UCT.
            if (( app.project.toolType != ToolType.Tool_CameraMaya) &&
                ( app.project.toolType != ToolType.Tool_CameraOrbit ) &&
                ( app.project.toolType != ToolType.Tool_CameraTrackXY) &&
                ( app.project.toolType != ToolType.Tool_CameraTrackZ))
                    app.project.toolType = ToolType.Tool_CameraMaya;
        }
    }

The following sample code uses the new app.project.toolType attribute to create a 360° composition (environment layer and camera) from a selected footage item or composition selected in the Project panel. This script a good starting point for building VR compositions from equirectangular footage::

    // Create a 360 VR comp from a footage item or comp selected in the Project panel.

    var item = app.project.activeItem;

    if (item != null && (item.typeName == "Footage" || item.typeName == "Composition")) {

        // Create a comp with the footage.
        var comp = app.project.items.addComp(item.name, item.width, item.height, item.pixelAspect, item.duration, item.frameRate);
        var layers = comp.layers;
        var footageLayer = layers.add(item);

        //Apply the CC Environment effect and create a camera.
        var effect = footageLayer.Effects.addProperty("CC Environment");
        var camera = layers.addCamera("360 Camera", [item.width/2, item.height/2]);
        comp.openInViewer(); app.project.toolType = ToolType.Tool_CameraMaya;
    }
    else {
        alert("Select a single footage item or composition in the Project panel.");
    }

----

.. _Project.transparencyGridThumbnails:

Project.transparencyGridThumbnails
*********************************************

``app.project.transparencyGridThumbnails``

**Description**

When true, thumbnail views use the transparency checkerboard pattern.

**Type**

Boolean; read/write.

----

.. _Project.xmpPacket:

Project.xmpPacket
*********************************************

``app.project.xmpPacket``

**Description**

The project’s XMP metadata, stored as RDF (XML-based). For more information on XMP, see the JavaScript Tools Guide.

**Type**

String; read/write.

**Example**

The following example code accesses the XMP metadata of the current project, and modifies the Label projectmetadata field.

::

    var proj = app.project;

    //load the XMPlibrary as an ExtendScript ExternalObject
    if(ExternalObject.AdobeXMPScript == undefined){
        ExternalObject.AdobeXMPScript = new ExternalObject('lib:AdobeXMPScript');
    }
    var mdata = new XMPMeta(app.project.xmpPacket); //get the project’s XMPmetadata
    //update the Label project metadata’s value
    var schemaNS = XMPMeta.getNamespaceURI("xmp");
    var propName = "xmp:Label";
    try{
        mdata.setProperty(schemaNS, propName, "finalversion...no, really!");
    }
    catch(e){
        alert(e);
    }
    app.project.xmpPacket = mdata.serialize();

----

=======
Methods
=======

.. _Project.autoFixExpressions:

Project.autoFixExpressions()
*********************************************

``app.project.autoFixExpressions(oldText, newText)``

**Description**

Automatically replaces text found in broken expressions in the project, if the new text causes the expression to evaluate without errors.

**Parameters**

===========  ======================
``oldText``  The text to replace.
``newText``  The new text.
===========  ======================

**Returns**

Nothing.

----

.. _project.close:

project.close()
*********************************************

``app.project.close(closeOptions)``

**Description**

Closes the project with the option of saving changes automatically, prompting the user to save changes or closing without saving changes.

**Parameters**

================  ============================================================
``closeOptions``  Action to be performed on close. A ``CloseOptions``
                  enumerated value, one of:

                  -  [``CloseOptions.DO_NOT_SAVE_CHANGES``: Close without
                     saving.
                  -  [``CloseOptions.PROMPT_TO_SAVE_CHANGES``:Prompt for
                     whether to save changes before close.
                  -  [``CloseOptions.SAVE_CHANGES``: Save automatically on
                     close.
================  ============================================================

**Returns**

Boolean. True on success. False if the file has not been previously saved, the user is prompted, and the user cancels the save.

----

.. _Project.consolidateFootage:

Project.consolidateFootage()
*********************************************

``app.project.consolidateFootage()``

**Description**

Consolidates all footage in the project. Same as the File > Consolidate All Footage command.

**Parameters**

None.

**Returns**

Integer; the total number of footage items removed.

----

.. _Project.importFile:

Project.importFile()
*********************************************

``app.project.importFile(importOptions)``

**Description**

Imports the file specified in the specified ImportOptions object, using the specified options. Same as the File > Import File command. Creates and returns a new FootageItem object from the file, and adds it to the project’s items array.

**Parameters**

=================   =====================================================
``importOptions``   An :ref:`ImportOptions` specifying the file to
                    import and the options for the operation.
=================   =====================================================

**Returns**

:ref:`FootageItem`.

**Example**

::

    app.project.importFile(new ImportOptions(File("sample.psd"))

----

.. _Project.importFileWithDialog:

Project.importFileWithDialog()
*********************************************

``app.project.importFileWithDialog()``

**Description**

Shows an Import File dialog box. Same as the File > Import > File command.

**Returns**

Array of :ref:`Item objects <item>` created during import; or null if the user cancels the dialog box.

----

.. _Project.importPlaceholder:

Project.importPlaceholder()
*********************************************

``app.project.importPlaceholder(name, width, height, frameRate, duration)``

**Description**

Creates and returns a new PlaceholderItem and adds it to the project’s items array. Same as the File > Import > Placeholder command.

**Parameters**

==============  ===============================================================
``name``        A string containing the name of the placeholder.
``width``       The width of the placeholder in pixels, an integer in the range
                ``[4..30000]``.
``height``      The height of the placeholder in pixels, an integer in the
                range ``[4..30000]``.
``frameRate``   The frame rate of the placeholder, a floating-point value in
                the range ``[1.0..99.0]``.
``duration``    The duration of the placeholder in seconds, a floating-point
                value in the range ``[0.0..10800.0]``.
==============  ===============================================================

**Returns**

PlaceholderItem object.

----

.. _Project.item:

Project.item()
*********************************************

``app.project.item(index)``

**Description**

Retrieves an item at a specified index position.

**Parameters**

=========  ====================================================================
``index``  The index position of the item, an integer. The first item is at
           index 1.
=========  ====================================================================

**Returns**

:ref:`Item`.

----

.. _Project.reduceProject:

Project.reduceProject()
*********************************************

``app.project.reduceProject(array_of_items)``

**Description**

Removes all items from the project except those specified. Same as the File > Reduce Project command.

**Parameters**

==================  ===========================================================
``array_of_items``  An array containing the :ref:`Item objects <item>` that are
                    to be kept.
==================  ===========================================================

**Returns**

Integer; the total number of items removed.

**Example**

::

    var theItems = new Array();
    theItems[theItems.length] = app.project.item(1);
    theItems[theItems.length] = app.project.item(3);
    app.project.reduceProject(theItems);

----

.. _Project.save:

Project.save()
*********************************************

``app.project.save([file])``

**Description**

Saves the project. The same as the File > Save or File > Save As command. If the project has never previously been saved and no file is specified, prompts the user for a location and file name. Pass a File object to save a project to a new file without prompting.

**Parameters**

========  ============================================================
``file``  Optional. An ExtendScript File object for the file to save.
========  ============================================================

**Returns**

None.

----

.. _Project.saveWithDialog:

Project.saveWithDialog()
*********************************************

``app.project.saveWithDialog()``

**Description**

Shows the Save dialog box. The user can name a file with a location and save the project, or click Cancel to exit the dialog box.

**Parameters**

None.

**Returns**

Boolean; true if the project was saved.

----

.. _Project.showWindow:

Project.showWindow()
*********************************************

``app.project.showWindow(doShow)``

**Description**

Shows or hides the Project panel.

**Parameters**

==========  ===================================================================
``doShow``  When true, show the Project panel. When false, hide the Project
            panel.
==========  ===================================================================

**Returns**

Nothing.
