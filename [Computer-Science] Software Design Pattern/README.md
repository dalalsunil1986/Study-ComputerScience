# ■ Software Design Pattern <kbd>[Kyungpook National University](http://www.knu.ac.kr/wbbs/)</kbd>


## ★ Model-View-Controller (MVC)

* 모델-뷰-컨트롤러(Model–View–Controller, MVC)는 소프트웨어 공학에서 사용되는 소프트웨어 디자인 패턴이다. 이 패턴을 성공적으로 사용하면, 사용자 인터페이스로부터 비즈니스 로직을 분리하여 애플리케이션의 시각적 요소나 그 이면에서 실행되는 비즈니스 로직을 서로 영향 없이 쉽게 고칠 수 있는 애플리케이션을 만들 수 있다. **MVC에서 모델은 애플리케이션의 정보(데이터)를 나타내며, 뷰는 텍스트, 체크박스 항목 등과 같은 사용자 인터페이스 요소를 나타내고, 컨트롤러는 데이터와 비즈니스 로직 사이의 상호동작을 관리한다.**

|:camera: Image 001|:camera: Image 002|:camera: Image 003|
|:-------:|:-------:|:-------:|
|![](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b5/ModelViewControllerDiagram2.svg/200px-ModelViewControllerDiagram2.svg.png)|![](https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Router-MVC-DB.svg/300px-Router-MVC-DB.svg.png)|![](https://koenig-media.raywenderlich.com/uploads/2016/04/diagram-mvc-480x241.png)|

* 컨트롤러는 모델에 명령을 보냄으로써 모델의 상태를 변경할 수 있다. (예: 워드 프로세서에서 문서를 편집하는 것) 또, 컨트롤러가 관련된 뷰에 명령을 보냄으로써 모델의 표시 방법을 바꿀 수 있다. (문서를 스크롤하는 것)

* 모델은 모델의 상태에 변화가 있을 때 컨트롤러와 뷰에 이를 통보한다. 이와 같은 통보를 통해서 뷰는 최신의 결과를 보여줄 수 있고, 컨트롤러는 모델의 변화에 따른 적용 가능한 명령을 추가·제거·수정할 수 있다. 어떤 MVC 구현에서는 통보 대신 뷰나 컨트롤러가 직접 모델의 상태를 읽어 오기도 한다.

* 뷰는 사용자가 볼 결과물을 생성하기 위해 모델로부터 정보를 얻어 온다.

* * *

#### ※ iOS Model-View-Controller (MVC) - [Model-View-Controller - Cocoa Core Competencies](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html)

* The Model-View-Controller (MVC) design pattern assigns objects in an application one of three roles: model, view, or controller. The pattern defines not only the roles objects play in the application, it defines the way objects communicate with each other. Each of the three types of objects is separated from the others by abstract boundaries and communicates with objects of the other types across those boundaries. The collection of objects of a certain MVC type in an application is sometimes referred to as a layer—for example, model layer.
</br></br> MVC is central to a good design for a Cocoa application. The benefits of adopting this pattern are numerous. Many objects in these applications tend to be more reusable, and their interfaces tend to be better defined. Applications having an MVC design are also more easily extensible than other applications. Moreover, many Cocoa technologies and architectures are based on MVC and require that your custom objects play one of the MVC roles.

###### ◈ Model Objects
* **Model objects encapsulate the data specific to an application and define the logic and computation that manipulate and process that data.** For example, a model object might represent a character in a game or a contact in an address book. A model object can have to-one and to-many relationships with other model objects, and so sometimes the model layer of an application effectively is one or more object graphs. Much of the data that is part of the persistent state of the application (whether that persistent state is stored in files or databases) should reside in the model objects after the data is loaded into the application. </br></br>Because model objects represent knowledge and expertise related to a specific problem domain, they can be reused in similar problem domains. Ideally, a model object should have no explicit connection to the view objects that present its data and allow users to edit that data—it should not be concerned with user-interface and presentation issues.

* Communication: User actions in the view layer that create or modify data are communicated through a controller object and result in the creation or updating of a model object. When a model object changes (for example, new data is received over a network connection), it notifies a controller object, which updates the appropriate view objects.

###### ◈ View Objects
* **A view object is an object in an application that users can see. A view object knows how to draw itself and can respond to user actions.** A major purpose of view objects is to display data from the application’s model objects and to enable the editing of that data. Despite this, view objects are typically decoupled from model objects in an MVC application. </br></br>Because you typically reuse and reconfigure them, view objects provide consistency between applications. Both the UIKit and AppKit frameworks provide collections of view classes, and Interface Builder offers dozens of view objects in its Library.

* Communication: View objects learn about changes in model data through the application’s controller objects and communicate user-initiated changes—for example, text entered in a text field—through controller objects to an application’s model objects.

###### ◈ Controller Objects
* **A controller object acts as an intermediary between one or more of an application’s view objects and one or more of its model objects.** Controller objects are thus a conduit through which view objects learn about changes in model objects and vice versa. Controller objects can also perform setup and coordinating tasks for an application and manage the life cycles of other objects.

* Communication: A controller object interprets user actions made in view objects and communicates new or changed data to the model layer. When model objects change, a controller object communicates that new model data to the view objects so that they can display it.

* * *

#### ※ Model-View-Controller Source Code (MVC) - [안드로이드의 MVC, MVP, MVVM 종합 안내서](https://academy.realm.io/kr/posts/eric-maxwell-mvc-mvp-and-mvvm-on-android/)

```swift
public class TicTacToeActivity extends AppCompatActivity {

    private Board model;

    /* View Components referenced by the controller */
    private ViewGroup buttonGrid;
    private View winnerPlayerViewGroup;
    private TextView winnerPlayerLabel;

    /**
     * In onCreate of the Activity we lookup & retain references to view components
     * and instantiate the model.
     */
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.tictactoe);
        winnerPlayerLabel = (TextView) findViewById(R.id.winnerPlayerLabel);
        winnerPlayerViewGroup = findViewById(R.id.winnerPlayerViewGroup);
        buttonGrid = (ViewGroup) findViewById(R.id.buttonGrid);

        model = new Board();
    }

    /**
     * Here we inflate and attach our reset button in the menu.
     */
    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        MenuInflater inflater = getMenuInflater();
        inflater.inflate(R.menu.menu_tictactoe, menu);
        return true;
    }
    /**
     *  We tie the reset() action to the reset tap event.
     */
    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        switch (item.getItemId()) {
            case R.id.action_reset:
                reset();
                return true;
            default:
                return super.onOptionsItemSelected(item);
        }
    }

    /**
     *  When the view tells us a cell is clicked in the tic tac toe board,
     *  this method will fire. We update the model and then interrogate it's state
     *  to decide how to proceed.  If X or O won with this move, update the view
     *  to display this and otherwise mark the cell that was clicked.
     */
    public void onCellClicked(View v) {

        Button button = (Button) v;

        int row = Integer.valueOf(tag.substring(0,1));
        int col = Integer.valueOf(tag.substring(1,2));

        Player playerThatMoved = model.mark(row, col);

        if(playerThatMoved != null) {
            button.setText(playerThatMoved.toString());
            if (model.getWinner() != null) {
                winnerPlayerLabel.setText(playerThatMoved.toString());
                winnerPlayerViewGroup.setVisibility(View.VISIBLE);
            }
        }

    }

    /**
     * On reset, we clear the winner label and hide it, then clear out each button.
     * We also tell the model to reset (restart) it's state.
     */
    private void reset() {
        winnerPlayerViewGroup.setVisibility(View.GONE);
        winnerPlayerLabel.setText("");

        model.restart();

        for( int i = 0; i < buttonGrid.getChildCount(); i++ ) {
            ((Button) buttonGrid.getChildAt(i)).setText("");
        }
    }
}
```

## ★ Model–View–ViewModel (MVVM)

* The well-ordered and perhaps the most reusable way to organize your code is to use the 'MVVM' pattern. The Model, View, ViewModel (MVVM pattern) is all about guiding you in how to organize and structure your code to write maintainable, testable and extensible applications.

* Model − It simply holds the data and has nothing to do with any of the business logic.

* ViewModel − It acts as the link/connection between the Model and View and makes stuff look pretty.

* View − It simply holds the formatted data and essentially delegates everything to the Model.

|MVVM Image 001|MVVM Image 002|MVVM Image 003|
|:------------:|:------------:|:------------:|
|![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/87/MVVMPattern.png/330px-MVVMPattern.png)|![](https://www.tutorialspoint.com/mvvm/images/separated_presentation.jpg)|![](https://koenig-media.raywenderlich.com/uploads/2018/04/MVVM_Diagram-480x197.png)|

## ★ REFERENCE

:airplane: [모델-뷰-컨트롤러(Model–View–Controller, MVC) - 위키백과](https://ko.wikipedia.org/wiki/%EB%AA%A8%EB%8D%B8-%EB%B7%B0-%EC%BB%A8%ED%8A%B8%EB%A1%A4%EB%9F%AC)

:airplane: [Model-View-Controller - Apple](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html)

:airplane: [Model-View-Controller (MVC) in iOS: A Modern Approach](https://www.raywenderlich.com/1073-model-view-controller-mvc-in-ios-a-modern-approach)

:airplane: [Model–view–viewmodel - 위키백과](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel)

:airplane: [안드로이드의 MVC, MVP, MVVM 종합 안내서 -Realm](https://academy.realm.io/kr/posts/eric-maxwell-mvc-mvp-and-mvvm-on-android/)

:airplane: [iOS 애플리케이션 아키텍처 : MVVM, MVC, VIPER 전격 비교 - Realm](https://academy.realm.io/kr/posts/krzysztof-zablocki-mDevCamp-ios-architecture-mvvm-mvc-viper/?w=1)
