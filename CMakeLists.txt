cmake_minimum_required(VERSION 3.15)

add_library(RmlLua STATIC
		Source/Lua/Colourb.cpp
		Source/Lua/Colourf.cpp
		Source/Lua/Context.cpp
		Source/Lua/ContextDocumentsProxy.cpp
		Source/Lua/Document.cpp
		Source/Lua/Element.cpp
		Source/Lua/ElementAttributesProxy.cpp
		Source/Lua/ElementChildNodesProxy.cpp
		Source/Lua/ElementInstancer.cpp
		Source/Lua/Elements/DataFormatter.cpp
		Source/Lua/Elements/DataSource.cpp
		Source/Lua/Elements/ElementDataGrid.cpp
		Source/Lua/Elements/ElementDataGridRow.cpp
		Source/Lua/Elements/ElementForm.cpp
		Source/Lua/Elements/ElementFormControl.cpp
		Source/Lua/Elements/ElementFormControlDataSelect.cpp
		Source/Lua/Elements/ElementFormControlInput.cpp
		Source/Lua/Elements/ElementFormControlSelect.cpp
		Source/Lua/Elements/ElementFormControlTextArea.cpp
		Source/Lua/Elements/ElementTabSet.cpp
		Source/Lua/Elements/LuaDataFormatter.cpp
		Source/Lua/Elements/LuaDataSource.cpp
		Source/Lua/Elements/SelectOptionsProxy.cpp
		Source/Lua/ElementStyleProxy.cpp
		Source/Lua/ElementText.cpp
		Source/Lua/Event.cpp
		Source/Lua/EventParametersProxy.cpp
		Source/Lua/GlobalLuaFunctions.cpp
		Source/Lua/Interpreter.cpp
		Source/Lua/Log.cpp
		Source/Lua/Lua.cpp
		Source/Lua/LuaDataModel.cpp
		Source/Lua/LuaDocument.cpp
		Source/Lua/LuaDocumentElementInstancer.cpp
		Source/Lua/LuaElementInstancer.cpp
		Source/Lua/LuaEventListener.cpp
		Source/Lua/LuaEventListenerInstancer.cpp
		Source/Lua/LuaPlugin.cpp
		Source/Lua/LuaType.cpp
		Source/Lua/RmlUi.cpp
		Source/Lua/RmlUiContextsProxy.cpp
		Source/Lua/Utilities.cpp
		Source/Lua/Vector2f.cpp
		Source/Lua/Vector2i.cpp
		)

target_compile_features(RmlLua PUBLIC cxx_std_17)
#target_compile_options(RXUtil PUBLIC -DRX_ASSET_DIR="${PROJECT_SOURCE_DIR}/assets")

if (MSVC)
	target_compile_options(RmlLua PRIVATE /W4 /wd4275 /wd4305 /wd4310 -D_CRT_SECURE_NO_WARNINGS -D_SILENCE_CXX17_OLD_ALLOCATOR_MEMBERS_DEPRECATION_WARNING -DWIN32_LEAN_AND_MEAN)
endif ()
target_compile_options(RmlLua PUBLIC -DRMLUI_STATIC_LIB)

target_include_directories(RmlLua PUBLIC "Source/Lua" Include)

target_link_libraries(RmlLua PUBLIC lua_static)

set_target_properties(RmlLua PROPERTIES
		CXX_STANDARD 17
		CXX_EXTENSIONS ON
		)

add_library(RmlCore STATIC
		Source/Core/BaseXMLParser.cpp
		Source/Core/Box.cpp
		Source/Core/Clock.cpp
		Source/Core/ComputeProperty.cpp
		Source/Core/Context.cpp
		Source/Core/ContextInstancer.cpp
		Source/Core/ContextInstancerDefault.cpp
		Source/Core/ConvolutionFilter.cpp
		Source/Core/Core.cpp
		Source/Core/DataController.cpp
		Source/Core/DataControllerDefault.cpp
		Source/Core/DataExpression.cpp
		Source/Core/DataModel.cpp
		Source/Core/DataModelHandle.cpp
		Source/Core/DataTypeRegister.cpp
		Source/Core/DataVariable.cpp
		Source/Core/DataView.cpp
		Source/Core/DataViewDefault.cpp
		Source/Core/Decorator.cpp
		Source/Core/DecoratorGradient.cpp
		Source/Core/DecoratorInstancer.cpp
		Source/Core/DecoratorNinePatch.cpp
		Source/Core/DecoratorTiled.cpp
		Source/Core/DecoratorTiledBox.cpp
		Source/Core/DecoratorTiledBoxInstancer.cpp
		Source/Core/DecoratorTiledHorizontal.cpp
		Source/Core/DecoratorTiledHorizontalInstancer.cpp
		Source/Core/DecoratorTiledImage.cpp
		Source/Core/DecoratorTiledImageInstancer.cpp
		Source/Core/DecoratorTiledInstancer.cpp
		Source/Core/DecoratorTiledVertical.cpp
		Source/Core/DecoratorTiledVerticalInstancer.cpp
		Source/Core/DocumentHeader.cpp
		Source/Core/Element.cpp
		Source/Core/ElementAnimation.cpp
		Source/Core/ElementBackgroundBorder.cpp
		Source/Core/ElementDecoration.cpp
		Source/Core/ElementDefinition.cpp
		Source/Core/ElementDocument.cpp
		Source/Core/ElementHandle.cpp
		Source/Core/ElementInstancer.cpp
		Source/Core/Elements/DataFormatter.cpp
		Source/Core/Elements/DataQuery.cpp
		Source/Core/Elements/DataSource.cpp
		Source/Core/Elements/DataSourceListener.cpp
		Source/Core/Elements/ElementDataGrid.cpp
		Source/Core/Elements/ElementDataGridCell.cpp
		Source/Core/Elements/ElementDataGridExpandButton.cpp
		Source/Core/Elements/ElementDataGridRow.cpp
		Source/Core/Elements/ElementForm.cpp
		Source/Core/Elements/ElementFormControl.cpp
		Source/Core/Elements/ElementFormControlDataSelect.cpp
		Source/Core/Elements/ElementFormControlInput.cpp
		Source/Core/Elements/ElementFormControlSelect.cpp
		Source/Core/Elements/ElementFormControlTextArea.cpp
		Source/Core/Elements/ElementImage.cpp
		Source/Core/Elements/ElementLabel.cpp
		Source/Core/Elements/ElementProgress.cpp
		Source/Core/Elements/ElementTabSet.cpp
		Source/Core/Elements/ElementTextSelection.cpp
		Source/Core/Elements/InputType.cpp
		Source/Core/Elements/InputTypeButton.cpp
		Source/Core/Elements/InputTypeCheckbox.cpp
		Source/Core/Elements/InputTypeRadio.cpp
		Source/Core/Elements/InputTypeRange.cpp
		Source/Core/Elements/InputTypeSubmit.cpp
		Source/Core/Elements/InputTypeText.cpp
		Source/Core/Elements/WidgetDropDown.cpp
		Source/Core/Elements/WidgetSlider.cpp
		Source/Core/Elements/WidgetTextInput.cpp
		Source/Core/Elements/WidgetTextInputMultiLine.cpp
		Source/Core/Elements/WidgetTextInputSingleLine.cpp
		Source/Core/Elements/WidgetTextInputSingleLinePassword.cpp
		Source/Core/Elements/XMLNodeHandlerDataGrid.cpp
		Source/Core/Elements/XMLNodeHandlerTabSet.cpp
		Source/Core/Elements/XMLNodeHandlerSelect.cpp
		Source/Core/Elements/XMLNodeHandlerTextArea.cpp
		Source/Core/ElementScroll.cpp
		Source/Core/ElementStyle.cpp
		Source/Core/ElementText.cpp
		Source/Core/ElementUtilities.cpp
		Source/Core/Event.cpp
		Source/Core/EventDispatcher.cpp
		Source/Core/EventInstancer.cpp
		Source/Core/EventInstancerDefault.cpp
		Source/Core/EventListenerInstancer.cpp
		Source/Core/EventSpecification.cpp
		Source/Core/Factory.cpp
		Source/Core/FileInterface.cpp
		Source/Core/FileInterfaceDefault.cpp
		Source/Core/FontEffect.cpp
		Source/Core/FontEffectBlur.cpp
		Source/Core/FontEffectGlow.cpp
		Source/Core/FontEffectInstancer.cpp
		Source/Core/FontEffectOutline.cpp
		Source/Core/FontEffectShadow.cpp
		Source/Core/FontEngineInterface.cpp
		Source/Core/Geometry.cpp
		Source/Core/GeometryBackgroundBorder.cpp
		Source/Core/GeometryDatabase.cpp
		Source/Core/GeometryUtilities.cpp
		Source/Core/LayoutBlockBox.cpp
		Source/Core/LayoutBlockBoxSpace.cpp
		Source/Core/LayoutDetails.cpp
		Source/Core/LayoutEngine.cpp
		Source/Core/LayoutInlineBox.cpp
		Source/Core/LayoutInlineBoxText.cpp
		Source/Core/LayoutLineBox.cpp
		Source/Core/LayoutTable.cpp
		Source/Core/LayoutTableDetails.cpp
		Source/Core/Log.cpp
		Source/Core/Math.cpp
		Source/Core/Memory.cpp
		Source/Core/ObserverPtr.cpp
		Source/Core/Plugin.cpp
		Source/Core/PluginRegistry.cpp
		Source/Core/Profiling.cpp
		Source/Core/PropertiesIteratorView.cpp
		Source/Core/Property.cpp
		Source/Core/PropertyDefinition.cpp
		Source/Core/PropertyDictionary.cpp
		Source/Core/PropertyParserAnimation.cpp
		Source/Core/PropertyParserColour.cpp
		Source/Core/PropertyParserDecorator.cpp
		Source/Core/PropertyParserFontEffect.cpp
		Source/Core/PropertyParserKeyword.cpp
		Source/Core/PropertyParserNumber.cpp
		Source/Core/PropertyParserRatio.cpp
		Source/Core/PropertyParserString.cpp
		Source/Core/PropertyParserTransform.cpp
		Source/Core/PropertySpecification.cpp
		Source/Core/RenderInterface.cpp
		Source/Core/Spritesheet.cpp
		Source/Core/Stream.cpp
		Source/Core/StreamFile.cpp
		Source/Core/StreamMemory.cpp
		Source/Core/StringUtilities.cpp
		Source/Core/StyleSheet.cpp
		Source/Core/StyleSheetContainer.cpp
		Source/Core/StyleSheetFactory.cpp
		Source/Core/StyleSheetNode.cpp
		Source/Core/StyleSheetNodeSelector.cpp
		Source/Core/StyleSheetNodeSelectorEmpty.cpp
		Source/Core/StyleSheetNodeSelectorFirstChild.cpp
		Source/Core/StyleSheetNodeSelectorFirstOfType.cpp
		Source/Core/StyleSheetNodeSelectorLastChild.cpp
		Source/Core/StyleSheetNodeSelectorLastOfType.cpp
		Source/Core/StyleSheetNodeSelectorNthChild.cpp
		Source/Core/StyleSheetNodeSelectorNthLastChild.cpp
		Source/Core/StyleSheetNodeSelectorNthLastOfType.cpp
		Source/Core/StyleSheetNodeSelectorNthOfType.cpp
		Source/Core/StyleSheetNodeSelectorOnlyChild.cpp
		Source/Core/StyleSheetNodeSelectorOnlyOfType.cpp
		Source/Core/StyleSheetParser.cpp
		Source/Core/StyleSheetSpecification.cpp
		Source/Core/SystemInterface.cpp
		Source/Core/Template.cpp
		Source/Core/TemplateCache.cpp
		Source/Core/Texture.cpp
		Source/Core/TextureDatabase.cpp
		Source/Core/TextureLayout.cpp
		Source/Core/TextureLayoutRectangle.cpp
		Source/Core/TextureLayoutRow.cpp
		Source/Core/TextureLayoutTexture.cpp
		Source/Core/TextureResource.cpp
		Source/Core/Transform.cpp
		Source/Core/TransformPrimitive.cpp
		Source/Core/TransformState.cpp
		Source/Core/TransformUtilities.cpp
		Source/Core/Tween.cpp
		Source/Core/TypeConverter.cpp
		Source/Core/URL.cpp
		Source/Core/Variant.cpp
		Source/Core/WidgetScroll.cpp
		Source/Core/XMLNodeHandler.cpp
		Source/Core/XMLNodeHandlerBody.cpp
		Source/Core/XMLNodeHandlerDefault.cpp
		Source/Core/XMLNodeHandlerHead.cpp
		Source/Core/XMLNodeHandlerTemplate.cpp
		Source/Core/XMLParser.cpp
		Source/Core/XMLParseTools.cpp

		Source/Core/FontEngineDefault/FontEngineInterfaceDefault.cpp
		Source/Core/FontEngineDefault/FontFace.cpp
		Source/Core/FontEngineDefault/FontFaceHandleDefault.cpp
		Source/Core/FontEngineDefault/FontFaceLayer.cpp
		Source/Core/FontEngineDefault/FontFamily.cpp
		Source/Core/FontEngineDefault/FontProvider.cpp
		Source/Core/FontEngineDefault/FreeTypeInterface.cpp
		)

target_compile_features(RmlCore PUBLIC cxx_std_17)
#target_compile_options(RXUtil PUBLIC -DRX_ASSET_DIR="${PROJECT_SOURCE_DIR}/assets")

if (MSVC)
	target_compile_options(RmlCore PRIVATE /W4 /wd4275 /wd4305 /wd4310 -D_CRT_SECURE_NO_WARNINGS -D_SILENCE_CXX17_OLD_ALLOCATOR_MEMBERS_DEPRECATION_WARNING -DWIN32_LEAN_AND_MEAN)
endif ()
target_compile_options(RmlCore PUBLIC -DRMLUI_STATIC_LIB)

target_include_directories(RmlCore PUBLIC "Source/Core" Include)
#target_link_libraries(RmlCore PUBLIC ../freetype/lib/freetype)

target_link_libraries(RmlCore PUBLIC freetype)

set_target_properties(RmlLua PROPERTIES
		CXX_STANDARD 17
		CXX_EXTENSIONS ON
		)


add_library(RmlDebugger STATIC
		Source/Debugger/Debugger.cpp
		Source/Debugger/DebuggerPlugin.cpp
		Source/Debugger/DebuggerSystemInterface.cpp
		Source/Debugger/ElementContextHook.cpp
		Source/Debugger/ElementInfo.cpp
		Source/Debugger/ElementLog.cpp
		Source/Debugger/Geometry.cpp
		)

target_compile_features(RmlDebugger PUBLIC cxx_std_20)
#target_compile_options(RXUtil PUBLIC -DRX_ASSET_DIR="${PROJECT_SOURCE_DIR}/assets")

if (MSVC)
	target_compile_options(RmlDebugger PRIVATE /W4 /wd4275 /wd4305 /wd4310 -D_CRT_SECURE_NO_WARNINGS -D_SILENCE_CXX17_OLD_ALLOCATOR_MEMBERS_DEPRECATION_WARNING -DWIN32_LEAN_AND_MEAN)
endif ()

target_compile_options(RmlDebugger PUBLIC -DRMLUI_STATIC_LIB)
target_include_directories(RmlDebugger PUBLIC "Source/Core" Include)

#target_link_libraries(RmlLua PUBLIC lua_static)

set_target_properties(RmlLua PROPERTIES
		CXX_STANDARD 17
		CXX_EXTENSIONS ON
		)
