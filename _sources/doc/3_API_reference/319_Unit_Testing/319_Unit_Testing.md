# Unit Testing

Unit tests validate the software by testing that the logic implemented inside a certain method, class, or module is working as expected. They should be as atomic and independent as possible.\
单元测试通过测试某个方法、类或模块内部实现的逻辑是否按预期运行来验证软件。单元测试应尽可能具有独立性。

Unit testing is highly important. The tests check that code changes are consistent with other parts of the code and verify that these changes are implemented properly.\
单元测试非常重要。单元测试检查代码更改是否与代码的其他部分保持一致，并验证这些更改是否正确实施。

Unit tests are in the [tests](https://github.com/pyansys/pymapdl/tree/main/tests) directory in this repository, along with integration tests. The difference between a unit test and an integration test is that the latter tests several units of the code to ensure that they all work together.\
单元测试和集成测试都在该版本库的 [tests](https://github.com/pyansys/pymapdl/tree/main/tests) 目录中。单元测试与集成测试的区别在于，后者测试多个单元的代码，以确保它们都能协同工作。

To verify that all code is properly tested, you must ensure that every piece of code is used (covered) in at least one unit test. In this repository, the [Codecov](https://github.com/codecov) tool generates a coverage report of the committed code. It details how merging a pull request would impact coverage. It is one of the checks that must run successfully to merge code changes.\
为了验证所有代码都经过了正确测试，您必须确保每一段代码都至少在一个单元测试中使用（覆盖）过。在该版本库中，[Codecov](https://github.com/codecov) 工具会生成已提交代码的覆盖率报告。它详细说明了合并拉取请求会如何影响覆盖率。这是合并代码变更时必须成功运行的检查之一。

```{figure}  /Images/3_API/codecov_increase.png
:align: center
:scale: 60%

**codecov_increase**
```

## Coverage example

To show how the coverage works, assume that you have this library:\
为了说明覆盖范围是如何工作的，假设您拥有这个库：

### My awesome library

```python
def get_report_colors(theme):
    if theme == "weather":
        colors = ["blue", "lightblue", "grey"]
    elif theme == "traffic":
        colors = ["red", "orange", "yellow"]
    else:
        colors = ["red", "blue", "green"]

    return colors
```

### Tests

You can opt to run the tests with this configuration:\
您可以选择以这种配置运行测试：

```python
def test_get_report_colors():
    assert get_report_colors("weather") == ["blue", "lightblue", "grey"]
    assert get_report_colors("traffic") == ["red", "orange", "yellow"]
    assert get_report_colors("other") == ["red", "blue", "green"]
```

Or, if a method is a bit more complex, you can split the case in different tests:\
或者，如果某个方法比较复杂，也可以将案例分成不同的测试：

```python
def test_get_report_colors_weather():
    assert get_report_colors("weather") == ["blue", "lightblue", "grey"]


def test_get_report_colors_traffic():
    assert get_report_colors("traffic") == ["red", "orange", "yellow"]


def test_get_report_colors_other():
    assert get_report_colors("other") == ["red", "blue", "green"]
```

While the code coverage in either case is 100% for the function, the second case is more useful for debugging the function.\
虽然两种情况下的代码覆盖率对函数来说都是 100%，但第二种情况对调试函数更有用。

## Continuous Integration and Continuous Deployment (CI/CD) approach 持续集成和持续部署（CI/CD）方法

Unit tests and integration tests are part of Continuous Integration (CI). The automation of testing, monitoring, and deployment of newly added code allows Continuous Deployment (CD) throughout the application lifecycle, providing a comprehensive CI/CD approach.\
单元测试和集成测试是持续集成（CI）的一部分。通过自动化测试、监控和部署新添加的代码，可以在整个应用程序生命周期内实现持续部署（CD），提供全面的 CI/CD 方法。


```{figure}  /Images/3_API/cicd.jpg
:align: center
:scale: 60%

**cicd**
```

## Creation of a unit test

In the PyMAPDL repository, [pytest](https://docs.pytest.org/en/7.2.x/) is used to run tests.\
在 PyMAPDL 代码库中，[pytest](https://docs.pytest.org/en/7.2.x/) 用于运行测试。

The name of a `pytest` file must be in the form `test_XXX.py`, where `XXX` is either the function, method, or class that you are testing or some other explicative name. In the command line, the `-k` argument can be used to filter the tests to run. For more information, see [pytest usage](https://docs.pytest.org/en/7.2.x/how-to/usage.html#specifying-which-tests-to-run).\
`pytest` 文件的名称必须是 `test_XXX.py` 形式，其中 `XXX` 可以是要测试的函数、方法或类，也可以是其他说明性名称。在命令行中，`-k` 参数可用于过滤要运行的测试。更多信息，请参阅 [pytest usage](https://docs.pytest.org/en/7.2.x/how-to/usage.html#specifying-which-tests-to-run)。

Here are some guidelines for creating good unit tests:\
下面是一些创建良好单元测试的指导原则：

- Assign long and descriptive names to tests.\为测试指定较长而具有描述性的名称。
- Use the [Codecov](https://github.com/codecov) tool to ensure all implemented code is tested.\使用 [Codecov](https://github.com/codecov) 工具确保所有执行的代码都经过测试。
- Check that tests return the same results each time.\检查每次测试的结果是否相同。
- Verify that tests are independent.\验证测试的独立性。
- Write tests that verify only one part of the code at a time.\编写测试，每次只验证代码的一部分。
- Make tests as short and fast as possible.\尽可能缩短测试时间，加快测试速度。

[What makes a good unit test](https://stackoverflow.com/questions/61400/what-makes-a-good-unit-test) is an exhaustive list of tips for creating good unit tests.\
`什么是好的单元测试` 详尽列举了创建好的单元测试的技巧。

Most PyMAPDL tests require a connection to a running instance of MAPDL, which makes them integration tests. If your test requires a running MAPDL instance, you can use the PyMAPDL [mapdl](https://github.com/pyansys/pymapdl/blob/fb5fb8b6201253f1bd56bdabee60a29abee8c7d8/tests/conftest.py#L254) method in your function signature. It will be executed upstream of each test and not within all tests.\
大多数 PyMAPDL 测试都需要连接到一个正在运行的 MAPDL 实例，这使得它们成为集成测试。如果您的测试需要一个运行中的 MAPDL 实例，您可以在函数签名中使用 PyMAPDL [mapdl](https://github.com/pyansys/pymapdl/blob/fb5fb8b6201253f1bd56bdabee60a29abee8c7d8/tests/conftest.py#L254) 方法。它将在每个测试的上游执行，而不是在所有测试中执行。

```python
def test_my_new_feature(mapdl):  # pass the 'mapdl' fixture as an argument.
    mapdl.prep7()
    # .... more code

    return True  # if everything goes ok until here
```

## Example

The [test_math.py](https://github.com/pyansys/pymapdl/blob/main/tests/test_math.py) file contains the unit tests and integration tests of the [ansys.mapdl.core.math module](https://mapdl.docs.pyansys.com/version/dev/user_guide/math.html). These are just some of the many tests that you can find in the [test directory](https://github.com/pyansys/pymapdl/tree/main/tests).\
test_math.py 文件包含 ansys.mapdl.core.math 模块的单元测试和集成测试。这些只是测试目录中众多测试的一部分。

Here are some examples of how you use `pytest`:

```pythoin
import numpy as np
import ansys.mapdl.core.math as apdl_math


@pytest.fixture(scope="module")
def mm(mapdl):  # pass the 'mapdl' fixture as an argument.
    return mapdl.math


def test_rand(mm):  # pass the 'mm' fixture as an argument.
    w = mm.rand(10)
    assert w.size == 10  # if it is False, AssertionError is raised


def test_matrix_addition(mm):
    m1 = mm.rand(10, 10)
    m2 = mm.rand(10, 10)
    m3 = m1 + m2
    assert np.allclose(m1.asarray() + m2.asarray(), m3.asarray())
    # if it is False, AssertionError is raised
```

For further explanations, see the [pytest documentation](https://docs.pytest.org/en/7.2.x/).

