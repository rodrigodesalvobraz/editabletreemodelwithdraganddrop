# Editable Tree Model with Drag and Drop

This is a version of the Qt 5.15.3 example [Editable Tree Model](https://doc.qt.io/qt-5/qtwidgets-itemviews-editabletreemodel-example.html)
modified to allow drag and drop, according to instructions in [Qt's documentation](https://doc.qt.io/qt-5/model-view-programming.html#using-model-view-classes).
It is currently *not* working properly: while one can drag and drop, the destination item shows as blank.

The changes relevant to drag and drop are [all gathered in this commit](https://github.com/rodrigodesalvobraz/editabletreemodelwithdraganddrop/commit/7ccaa8511ed95267499a3e8852a3450d41a06b53).

Note that the Qt documentation does describe the need to implement the dropMimeData method. However, the [source code of QAbstractItemModel](https://github.com/qt/qtbase/blob/52077d4f0193a236eacac98f75994b44a4c30a91/src/corelib/itemmodels/qabstractitemmodel.cpp#L2231) shows a default implementation for dropMimeData that should work. So it is unclear to me at the moment why this example is not working.

This [screen capture video shows the problem](https://github.com/rodrigodesalvobraz/editabletreemodelwithdraganddrop/blob/master/Editable%20Tree%20Model%20with%20Drag%20and%20Drop%20problem.mp4?raw=true).

