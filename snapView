import QtQuick 2.12
import QtQuick.Controls 2.5
import QtQuick.Layouts 1.14
import QtQml.Models 2.12

ApplicationWindow {
    id: applicationWindow
    visible: true
    width: 500
    height: 400
    opacity: 1
    Rectangle{
        id:leftRect
        width: 100
        height: parent.height
        color: "lightgreen"
        property alias litems: leftItems
        ListView{
            id:leftItems
            width: 100
            height: parent.height
            model: ListModel{
                ListElement{
                    myItemName:qsTr("network")
                }
                ListElement{
                    myItemName:qsTr("display")
                }
                ListElement{
                    myItemName:qsTr("more")
                }
            }
            highlight : Rectangle{
                color: "gray"
            }
            delegate:Rectangle{
                width: 100
                height: 30
                Text {
                    id: name
                    text: myItemName
                }
                color:"transparent"

                MouseArea{
                    anchors.fill: parent
                    hoverEnabled: true
                    onClicked: {
                        leftRect.litems.currentIndex = index
                        list.currentIndex = index
                    }
                }
            }
        }
    }
    ObjectModel{
        id:objModel
        Rectangle{
            width: list.width
            height: list.height
            color: "red"
        }
        Rectangle{
            width: list.width
            height: list.height
            color: "gray"
        }
        Rectangle{
            width: list.width
            height: list.height
            color: "blue"
        }
    }
    ListView{
        id:list
        width:400
        height:parent.height
        anchors.left: leftRect.right
        model:objModel
//        orientation: ListView.Horizontal
        clip: true //avoid lapping

        /* snapMode does not affect the currentIndex.
        * To update the currentIndex as the list is moved,
        * set highlightRangeMode to ListView.StrictlyEnforceRange.
        */
        snapMode: ListView.SnapOneItem
        highlightRangeMode:ListView.StrictlyEnforceRange
        onCurrentIndexChanged: {
            console.log("onCurrentIndexChanged ",currentIndex)
            if(leftRect.litems.currentIndex != currentIndex){
                leftRect.litems.currentIndex = currentIndex
            }
        }
    }

}
