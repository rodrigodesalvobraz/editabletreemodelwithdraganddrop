# Editable Tree Model with Drag and Drop

This is a version of the Qt 5.15.3 example [Editable Tree Model](https://doc.qt.io/qt-5/qtwidgets-itemviews-editabletreemodel-example.html)
modified to allow drag and drop, according to instructions in [Qt's documentation](https://doc.qt.io/qt-5/model-view-programming.html#using-model-view-classes).

There is a lot of misinformation online about drag and drop on Qt, and the documentation, while typically good, is rather confusing and incomplete on this topic.

I see that several users think they need to manually override the method `dropMimeData` to decode the undocumented, Qt-internal `x-qabstractitemmodeldatalist` MIME format, which is way too much work for such a commonplace functionality. The default method implementation takes care of that already.
Perhaps this confusion arises because the Qt documentation does describe the need to implement the `dropMimeData` method, but they must have meant it only in case the drag and drop operation is using some other MIME format, since the default one is, like I said, undocumented. In this example I did not re-implement it because the [source code of QAbstractItemModel](https://github.com/qt/qtbase/blob/52077d4f0193a236eacac98f75994b44a4c30a91/src/corelib/itemmodels/qabstractitemmodel.cpp#L2231) shows a default implementation for `dropMimeData` that works fine.

So I am posting this example in the hope that it helps the next person figuring this out in less time than me. I also intend to extend the example with `QTableView` and `QListView` to see if drag and drop will work without much setup there as well.

# An Initial Snag

I initially created this repository in order to ask for help, because just following the Qt documentation was not enough to get the example working. It turns out that the problem was in the model's `setData` method, which only dealt with the `EditRole` but needed to be extended to handle `DisplayRole` as well. In fact, I simply let it take all roles, and it works fine.

I've posted a very complete description of the problem as [a StackOverflow question](https://stackoverflow.com/questions/67292806/qt-attempt-to-add-drag-and-drop-to-editable-tree-model-example-not-working/67295984#67295984), and implemented the [needed correction on this commit](https://github.com/rodrigodesalvobraz/editabletreemodelwithdraganddrop/commit/a295f4f2d82d00cafae945f17238e2ef74d599ef).

The initial changes I made to implement drag and drop in the example (minus the fix described in the previous paragraph)
are [all gathered in this commit](https://github.com/rodrigodesalvobraz/editabletreemodelwithdraganddrop/commit/7ccaa8511ed95267499a3e8852a3450d41a06b53).
