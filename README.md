# CommonX
### Helper to handle Unity code scenarios
 ~ **CommonX** it's a DLL where you'll find methods to handle a variety of situations based of what you expect to when we are
making games on **Unity**

## How to Install
- You must have a **Unity Project**
- You must have to install **Git** (_https://git-scm.com/downloads_) (_Maybe you'll have to reboot after install_)
- Go to the **Package Manager** Window
- Click in the **'+' icon** 
- Click on the option **Add package from git URL...**
- Paste the git link: **https://github.com/kingdox/x-common** on it
- _Wait some seconds..._
- ___Installed 😎 👍___

## Helper Classes

- ### Supply
    _General class, this includes the most common methods._
    Frequently used methods:
    - **T Component<C, T>**: 
        Get the _Component_ and set on a ref variable, also allows you can chain methods, if it can't find it, you can add it too.
        Instead of:
        ```Button btn_back = gameObject.GetComponent<Button>(); ```
        ```btn_back.interactable = true;```
        ```btn_back.onClick.AddListener(Back);```
        Why not:
        ``` cs
            // Look you're not typing any type, because is implicit on the variable 'btn_back'
            this.Component(out btn_back).interactable = true; 
            btn_back.onClick.AddListener(Back);
        ```
    - **T[] Components<T>**: 
        Get the same _Component_ of every child of a _Transform_ (Excluding itself)
        example:
        ``` cs
            //Where 'btn_buyItems' represent a Button[]
            this.Components(out btn_buyItems);
        ```
    - **void ClearChilds**: 
        Destroy every _GameObject_ child of a _Transform_ parent
        example:
        ``` cs
            transform_parentItems.ClearChilds();
        ```
    - **void Singleton<T>**:
        Apply the Singleton Pattern, also can include a Object.DontDestroyOnLoad
        example:
        ``` cs
            //'this' means the class to be unique and instance means the static variable of the Type
            this.Singleton(ref instance);
        ```
    - **Lenght<T>()**:
        Returns the _Qty_ of key elements on a _Enum_
        ``` cs
        enum WordType{
            A = -1,
            B = 2,
            C = 0
        }
        //returns 3
        Supply.Lenght<WordType>(); 
        ```
    - **T Print<T>()**:
        One of the most useful Methods, Used to debug whenever you want, adding a Color if you want (or a random)
        ``` cs
        int a = 1;
        int b = 2;
        int c = 3;
        //Look that you can add it in each part of your code, this is useful when you whant to debug each piece of code on a specified moment without any alteration of the formula
        int result = ((2*b).Print("red") / (a-c).Print("blue"));
        string displayedResult = $"on a:{a},b:{b} and c:{c}, \n the result is {result}".Print("magenta");
        return displayedResult;
        ```
- ### Get.Get
    _Class based on obtention of data_
    Frequently used methods:
    - **T Any<T>()**: 
    Returns any item of an _Array_
    ``` cs
     Transform tr_target = tr_targets.Any();
    ```
    - **int ZeroMax()**: 
    Returns a random value betweeen 0 and the specified int
    ``` cs
    100.ZeroMax();
    100f.ZeroMax();
    array.ZeroMax();
    ```
    - **float Max()**: 
    returns a value clamped on the Max value
    ``` cs
    int percent = value.Max(100);
    ```
    - **float Min()**: 
    returns a value clamped on the Min value
    ``` cs
    int life = (life - damage).Min(0);
    ```