# WPFでコードビハインドとバインド

XAML側

```xml
<TextBox Text="{Binding Foo}"/>
```

コード側

```cs
public partial class FooClass : UserControl
{
    public string Foo { get; set; }

    public FooClass()
    {
        InitializeComponent();
        DataContext = this;
    }
}
```

コード側では以下が必須。

- バインドするプロパティをpublicにする
- バインドするプロパティにgetterとsetterを定義する
- コンストラクタ内で `DataContext = this;`
