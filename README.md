# freecad installation
ubuntu 20.04
```
sudo snap install
sudo snap install qt515-core20
```
add this line in .bashrc with:
```
export LD_LIBRARY_PATH="/snap/freecad/current/usr/lib/:/snap/freecad/current/usr/lib/x86_64-linux-gnu/:/snap/qt515-core20/26/opt/qt515/lib/:$LD_LIBRARY_PATH"
```
An example file to draw a cube:

```
import os, sys
sys.path.insert(0, "/snap/freecad/517/usr/lib")
sys.path.insert(0, "/snap/freecad/517/usr/lib/python3/dist-packages")

from PySide2 import QtCore, QtGui, QtWidgets
import FreeCAD, FreeCADGui
import Robot

class MainWindow(QtWidgets.QMainWindow):
    def showEvent(self, event):
        FreeCADGui.showMainWindow()
        self.setCentralWidget(FreeCADGui.getMainWindow())

app=QtWidgets.QApplication(sys.argv)
mw=MainWindow()
mw.resize(1200,800)
mw.show()

import Part
cube = Part.makeBox(2,2,2)
# creates a document and a Part feature with the cube
Part.show(cube)
app.exec_()
```
