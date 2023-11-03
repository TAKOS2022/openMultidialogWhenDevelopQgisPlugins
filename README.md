# openMultidialogWhenDevelopQgisPlugins
This repository show how to manage multi dialog when we develop Qgis Plugins

Step : 
- Open Qt designer and create a new form
- Save it where the main winform are save
- Open pb_tool.cfg
- Go to # Other ui files for dialogs you create (these will be compiled)
- Past the name of the new ui : compiled_ui_files: newform.ui
- Save it
- Open OsGeo shell and run pb_tool clean --> pb_tool clean --> pb_tool deploy : You should see newform.py appear in the directory
- (Optionnaly : run pyrcc5 -o resources_rc.py resources.qrc)
- Open your plugin_dialog.py and import the newfrom.py : from .newfrom import ui_newform
- Create a fonction :
  def open_server_info_dialog(self):
        self.server_info_dialog = QtWidgets.QDialog()
        ui = Ui_ServerInfoDialog()
        ui.setupUi(self.server_info_dialog)
        self.server_info_dialog.exec_()
  - Go to method init of plugin_dialog.py and call that fonction 
