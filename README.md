import random
import sys
import time

from PyQt5 import QtCore, QtGui, QtWidgets
from PyQt5.QtCore import *
from PyQt5.QtGui import *
from PyQt5.QtWidgets import *
from PyQt5.QtWidgets import QWidget, QLabel, QPushButton
from PyQt5.QtWidgets import QApplication, QMainWindow


Min = "&#128163;"
flag = "&#128681;"

Starting = "&#128578;"
World_time = "&#9200;"

COLORS = {1: QColor('#f44336'),
          2: QColor('#9C27B0'),
          3: QColor('#3F51B5'),
          4: QColor('#03A9F4'),
          5: QColor('#00BCD4'),
          6: QColor('#4CAF50'),
          7: QColor('#E91E63'),
          8: QColor('#FF9800')}


READY = 0
PLAYING = 1
FAILED = 20
SUCCESS = 3

HOLST = {READY: "&#128512;",
         PLAYING: "&#128517;",
         FAILED: "&#128532;",
         SUCCESS: "&#128515;"}


class Begin1(QWidget):

    def setupUi(self, logic):
        logic.setObjectName("deuxieme")
        logic.resize(800, 600)

        self.centralwidget = QtWidgets.QWidget(logic)
        self.centralwidget.setObjectName("central")

        self.label = QtWidgets.QListWidget(self.centralwidget)
        self.label.setGeometry(QtCore.QRect(230, 70, 340, 71))
        font = QtGui.QFont()
        font.setPointSize(30)

        self.label.setFont(font)
        self.label.setObjectName("listWidget")
        item = QtWidgets.QListWidgetItem()
        self.label.addItem(item)

        self.pushButton = QtWidgets.QPushButton(self.centralwidget)
        self.pushButton.setGeometry(QtCore.QRect(330, 260, 75, 23))
        self.pushButton.setObjectName("pushButton")
        logic.setCentralWidget(self.centralwidget)

        self.menubar = QtWidgets.QMenuBar(logic)
        self.menubar.setGeometry(QtCore.QRect(0, 0, 800, 21))
        self.menubar.setObjectName("menubar")
        logic.setMenuBar(self.menubar)

        self.status_job = QtWidgets.QStatusBar(logic)
        self.status_job.setObjectName("statusbar")
        logic.setStatusBar(self.status_job)

        self.retranslateUi(logic)
        QtCore.QMetaObject.connectSlotsByName(logic)

    def retranslateUi(self, logic):
        _translate = QtCore.QCoreApplication.translate
        logic.setWindowTitle(_translate("MainWindow", "MainWindow"))
        __sortingEnabled = self.label.isSortingEnabled()
        self.label.setSortingEnabled(False)
        item = self.label.item(0)
        item.setText(_translate("MainWindow", "Подводные мины"))
        self.label.setSortingEnabled(__sortingEnabled)
        self.pushButton.setText(_translate("MainWindow", "Пуск"))
        self.pushButton.clicked.connect(self.show_window_2)


class MyWidget2(QMainWindow, Begin1):
    def __init__(self):
        super().__init__()
        self.setupUi(self)
        self.pushButton.clicked.connect(self.show_window_2)

    def show_window_2(self):
        self.w2 = MyWidget1()
        self.w2.show()


class Begin2(QWidget):

    def setupUi(self, Pop):
        Pop.setObjectName("MainWindow")
        Pop.resize(700, 500)

        self.table = QtWidgets.QWidget(Pop)
        self.table.setObjectName("table")

        self.listWidget = QtWidgets.QListWidget(self.table)
        self.listWidget.setGeometry(QtCore.QRect(230, 90, 211, 71))

        font = QtGui.QFont()
        font.setPointSize(30)

        self.listWidget.setFont(font)
        self.listWidget.setObjectName("listWidget")

        item = QtWidgets.QListWidgetItem()
        self.listWidget.addItem(item)

        self.doing = QtWidgets.QPushButton(self.table)
        self.doing.setGeometry(QtCore.QRect(290, 270, 75, 23))
        self.doing.setObjectName("doing")

        self.horizontalLayoutWidget = QtWidgets.QWidget(self.table)
        self.horizontalLayoutWidget.setGeometry(QtCore.QRect(230, 180, 211, 41))
        self.horizontalLayoutWidget.setObjectName("horizontalLayoutWidget")

        self.number_one = QtWidgets.QHBoxLayout(self.horizontalLayoutWidget)
        self.number_one.setContentsMargins(0, 0, 0, 0)
        self.number_one.setObjectName("number_one")
        self.name_boom = QtWidgets.QLabel(self.horizontalLayoutWidget)

        font = QtGui.QFont()
        font.setPointSize(16)

        self.name_boom.setFont(font)
        self.name_boom.setObjectName("name_boom")
        self.number_one.addWidget(self.name_boom)

        self.boom = QtWidgets.QSpinBox(self.horizontalLayoutWidget)
        self.boom.setToolTipDuration(1)
        self.boom.setMinimum(1)
        self.boom.setMaximum(20)
        self.boom.setProperty("value", 20)
        self.boom.setObjectName("boom")
        self.number_one.addWidget(self.boom)

        self.horizontalLayoutWidget_2 = QtWidgets.QWidget(self.table)
        self.horizontalLayoutWidget_2.setGeometry(QtCore.QRect(230, 219, 211, 41))
        self.horizontalLayoutWidget_2.setObjectName("horizontalLayoutWidget_2")

        self.number_2 = QtWidgets.QHBoxLayout(self.horizontalLayoutWidget_2)
        self.number_2.setContentsMargins(0, 0, 0, 0)
        self.number_2.setObjectName("number_2")
        self.name_square = QtWidgets.QLabel(self.horizontalLayoutWidget_2)

        font = QtGui.QFont()
        font.setPointSize(16)

        self.name_square.setFont(font)
        self.name_square.setObjectName("name_square")
        self.number_2.addWidget(self.name_square)

        self.Ox = QtWidgets.QSpinBox(self.horizontalLayoutWidget_2)
        self.Ox.setToolTipDuration(5)
        self.Ox.setProperty("value", 10)
        self.Ox.setObjectName("Ox")
        self.number_2.addWidget(self.Ox)

        self.Oy = QtWidgets.QSpinBox(self.horizontalLayoutWidget_2)
        self.Oy.setToolTipDuration(5)
        self.Oy.setProperty("value", 10)
        self.Oy.setObjectName("Oy")
        self.number_2.addWidget(self.Oy)

        Pop.setCentralWidget(self.table)
        self.menubar = QtWidgets.QMenuBar(Pop)
        self.menubar.setGeometry(QtCore.QRect(0, 0, 462, 21))
        self.menubar.setObjectName("menubar")

        Pop.setMenuBar(self.menubar)
        self.statusbar = QtWidgets.QStatusBar(Pop)

        palette = QtGui.QPalette()

        brush = QtGui.QBrush(QtGui.QColor(125, 215, 189))
        brush.setStyle(QtCore.Qt.SolidPattern)

        palette.setBrush(QtGui.QPalette.Active, QtGui.QPalette.Highlight, brush)

        brush = QtGui.QBrush(QtGui.QColor(125, 215, 189))
        brush.setStyle(QtCore.Qt.SolidPattern)

        palette.setBrush(QtGui.QPalette.Inactive, QtGui.QPalette.Highlight, brush)

        brush = QtGui.QBrush(QtGui.QColor(0, 120, 215))
        brush.setStyle(QtCore.Qt.SolidPattern)

        palette.setBrush(QtGui.QPalette.Disabled, QtGui.QPalette.Highlight, brush)

        self.statusbar.setPalette(palette)
        self.statusbar.setObjectName("statusbar")
        Pop.setStatusBar(self.statusbar)

        self.retranslateUi(Pop)
        QtCore.QMetaObject.connectSlotsByName(Pop)

    def retranslateUi(self, Pop):
        _translate = QtCore.QCoreApplication.translate
        Pop.setWindowTitle(_translate("MainWindow", "MainWindow"))
        __sortingEnabled = self.listWidget.isSortingEnabled()
        self.listWidget.setSortingEnabled(False)

        item = self.listWidget.item(0)
        item.setText(_translate("MainWindow", "Настройки"))
        self.listWidget.setSortingEnabled(__sortingEnabled)

        self.doing.setText(_translate("MainWindow", "Пуск"))
        self.doing.clicked.connect(self.show_window_3)

        self.name_boom.setText(_translate("MainWindow", "Мины:"))
        self.name_square.setText(_translate("MainWindow", "Площадь:"))


class MyWidget1(QMainWindow, Begin2):
    def __init__(self):
        super().__init__()
        self.setupUi(self)
        self.doing.clicked.connect(self.show_window_3)

    def show_window_3(self):
        self.w3 = Game()
        self.w3.show()


class Game(QMainWindow, Begin2):
    def __init__(self, *args, **kwargs):
        super(Game, self).__init__(*args, **kwargs)

        self.Tile = Begin2()
        self.TABLE1, self.TABLE2, self.BOMBES = self.Ox.text(), self.Oy.text(), self.boom.text()

        kolling = QWidget()
        wonder = QHBoxLayout()

        self.bombes = QLabel()
        self.bombes.setAlignment(Qt.AlignHCenter | Qt.AlignVCenter)

        self.clock = QLabel()
        self.clock.setAlignment(Qt.AlignHCenter | Qt.AlignVCenter)

        did = self.bombes.font()
        did.setPointSize(24)
        did.setWeight(75)
        self.bombes.setFont(did)
        self.clock.setFont(did)

        self.tic = QTimer()
        self.tic.timeout.connect(self.My_time)
        self.tic.start(1000)

        self.bombes.setText("%03d" % self.BOMBES)
        self.clock.setText("000")

        self.button = QPushButton()
        self.button.setFixedSize(QSize(32, 32))
        self.button.setIconSize(QSize(32, 32))
        self.button.setIcon("&#128579")
        self.button.setFlat(True)

        self.button.pressed.connect(self.Start)

        good = QLabel()
        good.setPixmap(QPixmap.fromImage(Min))
        good.setAlignment(Qt.AlignRight | Qt.AlignVCenter)
        wonder.addWidget(good)

        wonder.addWidget(self.bombes)
        wonder.addWidget(self.button)
        wonder.addWidget(self.clock)

        good = QLabel()
        good.setPixmap(QPixmap.fromImage(World_time))
        good.setAlignment(Qt.AlignLeft | Qt.AlignVCenter)
        wonder.addWidget(good)

        vrb = QVBoxLayout()
        vrb.addLayout(wonder)

        self.hope = QGridLayout()
        self.hope.setSpacing(5)

        vrb.addLayout(self.hope)
        kolling.setLayout(vrb)
        self.setCentralWidget(kolling)

        self.picture()
        self.work(READY)

        self.norrmal()
        self.work(READY)

        self.show()

    def work(self, hoe):
        self.hoe = hoe
        self.button.setIcon(QIcon(HOLST[self.hoe]))

    def Start(self):
        if self.hoe == PLAYING:
            self.work(FAILED)
            self.doing()

        elif self.hoe == FAILED:
            self.work(READY)
            self.norrmal()

    def picture(self):
        for x in range(0, self.TABLE1):
            for y in range(0, self.TABLE2):
                fail = Game(x, y)
                self.hope.addWidget(fail, y, x)
                fail.konecked.connect(self.logic)
                fail.selling.connect(self.name_root)
                fail.hole.connect(self.The_end)

    def more_logic(self, x, y):
        destinationer = []

        for i in range(max(0, x - 1), min(x + 2, self.TABLE1)):
            for j in range(max(0, y - 1), min(y + 2, self.TABLE2)):
                destinationer.append(self.hope.itemAtPosition(j, i).widget())

        return destinationer

    def My_time(self):
        if self.hoe == PLAYING:
            royal = int(time.time()) - self.starting_time
            self.clock.setText("%03d" % royal)

    def norrmal(self):
        for x in range(0, self.TABLE1):
            for y in range(0, self.TABLE2):
                job = self.hope.itemAtPosition(y, x).widget()
                job.reset()

        destination = []
        while len(destination) < self.BOMBES:
            x, y = random.randint(0, self.TABLE1 - 1), random.randint(0, self.TABLE2 - 1)
            if (x, y) not in destination:
                hope = self.hope.itemAtPosition(y, x).widget()
                hope.min = True
                destination.append((x, y))

        def My_voice(x, y):
            destinationer = self.more_logic(x, y)
            BOMBES = sum(1 if kolling.min else 0 for kolling in destinationer)

            return BOMBES

        for x in range(0, self.TABLE1):
            for y in range(0, self.TABLE2):
                kolling = self.hope.itemAtPosition(y, x).widget()
                kolling.kol = My_voice(x, y)

        while True:
            x, y = random.randint(0, self.TABLE1 - 1), random.randint(0, self.TABLE2 - 1)
            kolling = self.hope.itemAtPosition(y, x).widget()

            if (x, y) not in destination:
                kolling = self.hope.itemAtPosition(y, x).widget()
                kolling.tragic = True

                for kolling in self.more_logic(x, y):
                    if not kolling.min:
                        kolling.click()
                break

    def doing(self):
        for x in range(0, self.TABLE1):
            for y in range(0, self.TABLE2):
                w = self.hope.itemAtPosition(y, x).widget()
                w.reveal()

    def name_root(self, x, y):
        for i in range(max(0, x - 1), min(x + 2, self.TABLE1)):
            for j in range(max(0, y - 1), min(y + 2, self.TABLE2)):
                kolling = self.hope.itemAtPosition(j, i).widget()
                if not kolling.min:
                    kolling.click()

    def logic(self):
        if self.hoe != PLAYING:
            self.work(PLAYING)
            self.starting_time = int(time.time())

    def The_end(self):
        self.doing()
        self.work(FAILED)


class Game23(QWidget):
    selling = pyqtSignal(int, int)
    konecked = pyqtSignal()
    hole = pyqtSignal()

    def __init__(self, x, y, *args, **kwargs):
        super(Game23, self).__init__(*args, **kwargs)

        self.setFixedSize(QSize(20, 20))

        self.x = x
        self.y = y

    def tabs(self, click):

        if (click.button() == Qt.RightButton and not self.tir):
            self.my_game()

        elif (click.button() == Qt.LeftButton):
            self.relise()

            if self.mine:
                self.hole.emit()

    def relise(self):
        if not self.tir:
            self.modern()
            if self.kol == 0:
                self.expandable.emit(self.x, self.y)

        self.konecked.emit()

    def modern(self):
        self.tir = True
        self.update()

    def my_game(self):
        self.SHlag = True
        self.update()

        self.konecked.emit()

    def choosing(self):
        self.tir = False
        self.start = False
        self.kol = 0

        self.SHlag = False
        self.mine = False

        self.update()

    def like(self, tr):
        world = QPainter(self)
        world.setRenderHint(QPainter.Antialiasing)

        zero = tr.rect()

        if self.tir:
            color = self.palette().color(QPalette.Background)
            outer, inner = color, color
        else:
            outer, inner = Qt.gray, Qt.lightGray

        world.fillRect(zero, QBrush(inner))
        pen = QPen(outer)
        pen.setWidth(1)
        world.setPen(pen)
        world.drawRect(zero)

        if self.tir:
            if self.start:
                world.drawPixmap(zero, QPixmap(Starting))

            elif self.mine:
                world.drawPixmap(zero, QPixmap(Min))

            elif self.kol > 0:
                pen = QPen(COLORS[self.kol])
                world.setPen(pen)
                named = world.font()
                named.setBold(True)
                world.setFont(named)
                world.drawText(zero, Qt.AlignHCenter | Qt.AlignVCenter, str(self.kol))

        elif self.SHlag:
            world.drawPixmap(zero, QPixmap(flag))


if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = MyWidget2()
    ex.show()
    sys.exit(app.exec_())
