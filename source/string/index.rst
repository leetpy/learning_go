字符串操作
==========

字符串拼接
----------

.. code-block:: go

    // 直接相加
    s1 := "hello" + "world"

    // 格式化
    s2 := fmt.Sprintf("%s%s", "hello", "world")

    // strings.Join
    var strList []string = []string{"hello", "world"}
    s3 := strings.Join(strList, "")

    // buffer.WriteString
    var bt bytes.Buffer
    bt.WriteString("hello")
    bt.WriteString("world")
    s4 := bt.String()

    // strings.Builder, 和 WriteString 差不多，不过官方推荐这种方式
    var build strings.Builder
    build.WriteString("hello")
    build.WriteString("world")
    s5 := build.String()