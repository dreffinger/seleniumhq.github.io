---
title: "選択要素の操作"
linkTitle: "選択要素の操作"
weight: 2
aliases: ["/documentation/ja/support_packages/working_with_select_elements/"]
---


一部の要素では、自動化するためにかなりのボイラープレートコードが必要になる場合があります。
これを減らしてテストをきれいにするために、Seleniumサポートパッケージに `Select` クラスがあります。
それを使用するには、次のimportステートメントが必要です。

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
import org.openqa.selenium.support.ui.Select;
  {{< /tab >}}
  {{< tab header="Python" >}}
from selenium.webdriver.support.select import Select
  {{< /tab >}}
  {{< tab header="CSharp" >}}
using OpenQA.Selenium.Support.UI
  {{< /tab >}}
  {{< tab header="Ruby" >}}
include Selenium::WebDriver::Support
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
// This feature is not implemented - Help us by sending a pr to implement this feature 
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
import org.openqa.selenium.support.ui.Select
  {{< /tab >}}
{{< /tabpane >}}

そして、 `<select>` 要素を参照するWebElementを使用してSelectオブジェクトを作成できます。

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
WebElement selectElement = driver.findElement(By.id("selectElementID"));
Select selectObject = new Select(selectElement);
  {{< /tab >}}
  {{< tab header="Python" >}}
select_element = driver.find_element(By.ID,'selectElementID')
select_object = Select(select_element)
  {{< /tab >}}
  {{< tab header="CSharp" >}}
IWebElement selectElement = driver.FindElement(By.Id("selectElementID"));
var selectObject = new SelectElement(selectElement);
  {{< /tab >}}
  {{< tab header="Ruby" >}}
select_element = driver.find_element(id: 'selectElementID')
select_object = Select(select_element)
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
// This feature is not implemented - Help us by sending a pr to implement this feature
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
val selectElement = driver.findElement(By.id("selectElementID"))
val selectObject = new Select(selectElement)
  {{< /tab >}}
{{< /tabpane >}}

Selectオブジェクトは、 `<select>` 要素とやり取りできる一連のコマンドを提供します。
まず、 `<select>` 要素からオプションを選択するさまざまな方法があります。

```html
<select>
 <option value=value1>Bread</option>
 <option value=value2 selected>Milk</option>
 <option value=value3>Cheese</option>
</select>
```

上記の要素から最初のオプションを選択するには、3つの方法があります。

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
// Select an <option> based upon the <select> element's internal index
selectObject.selectByIndex(1);

// Select an <option> based upon its value attribute
selectObject.selectByValue("value1");

// Select an <option> based upon its text
selectObject.selectByVisibleText("Bread");
  {{< /tab >}}
  {{< tab header="Python" >}}
# Select an <option> based upon the <select> element's internal index
select_object.select_by_index(1)

# Select an <option> based upon its value attribute
select_object.select_by_value('value1')

# Select an <option> based upon its text
select_object.select_by_visible_text('Bread')
  {{< /tab >}}
  {{< tab header="CSharp" >}}
// Select an <option> based upon the <select> element's internal index
selectObject.SelectByIndex(1);

// Select an <option> based upon its value attribute
selectObject.SelectByValue("value1");

// Select an <option> based upon its text
 selectObject.SelectByText("Bread");
  {{< /tab >}}
  {{< tab header="Ruby" >}}
# Select an <option> based upon the <select> element's internal index
select_object.select_by(:index, 1)

# Select an <option> based upon its value attribute
select_object.select_by(:value, 'value1')

# Select an <option> based upon its text
select_object.select_by(:text, 'Bread')
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
// This feature is not implemented - Help us by sending a pr to implement this feature
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
// Select an <option> based upon the <select> element's internal index
selectObject.selectByIndex(1)

// Select an <option> based upon its value attribute
selectObject.selectByValue("value1")

// Select an <option> based upon its text
selectObject.selectByVisibleText("Bread")
  {{< /tab >}}
{{< /tabpane >}}

以下を使用して、選択されているオプションを確認できます。

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
// Return a List<WebElement> of options that have been selected
List<WebElement> allSelectedOptions = selectObject.getAllSelectedOptions();

// Return a WebElement referencing the first selection option found by walking down the DOM
WebElement firstSelectedOption = selectObject.getFirstSelectedOption();
  {{< /tab >}}
  {{< tab header="Python" >}}
# Return a list[WebElement] of options that have been selected
all_selected_options = select_object.all_selected_options

# Return a WebElement referencing the first selection option found by walking down the DOM
first_selected_option = select_object.first_selected_option
  {{< /tab >}}
  {{< tab header="CSharp" >}}
// Return a List<WebElement> of options that have been selected
var allSelectedOptions = selectObject.AllSelectedOptions;

// Return a WebElement referencing the first selection option found by walking down the DOM
var firstSelectedOption = selectObject.AllSelectedOptions.FirstOrDefault();
  {{< /tab >}}
  {{< tab header="Ruby" >}}
# Return an Array[Element] of options that have been selected
all_selected_options = select_object.selected_options

# Return a WebElement referencing the first selection option found by walking down the DOM
first_selected_option = select_object.first_selected_option
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
// This feature is not implemented - Help us by sending a pr to implement this feature
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
// Return a List<WebElement> of options that have been selected
val allSelectedOptions = selectObject.allSelectedOptions

// Return a WebElement referencing the first selection option found by walking down the DOM
val firstSelectedOption = selectObject.firstSelectedOption
  {{< /tab >}}
{{< /tabpane >}}

または、 `<select>` 要素に含まれる `<option>` 要素に興味があるかもしれません。

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
// Return a List<WebElement> of options that the <select> element contains
List<WebElement> allAvailableOptions = selectObject.getOptions();
  {{< /tab >}}
  {{< tab header="Python" >}}
# Return a list[WebElement] of options that the &lt;select&gt; element contains
all_available_options = select_object.options
  {{< /tab >}}
  {{< tab header="CSharp" >}}
// Return a IList<IWebElement> of options that the <select> element contains
IList<IWebElement> allAvailableOptions = selectObject.Options;
  {{< /tab >}}
  {{< tab header="Ruby" >}}
# Return an Array[Element] of options that the &lt;select&gt; element contains
all_available_options = select_object.options
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
// This feature is not implemented - Help us by sending a pr to implement this feature
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
// Return a List<WebElement> of options that the <select> element contains
val allAvailableOptions = selectObject.options
  {{< /tab >}}
{{< /tabpane >}}

要素の選択を解除する場合は、4つの選択肢があります。

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
// Deselect an <option> based upon the <select> element's internal index
selectObject.deselectByIndex(1);

// Deselect an <option> based upon its value attribute
selectObject.deselectByValue("value1");

// Deselect an <option> based upon its text
selectObject.deselectByVisibleText("Bread");

// Deselect all selected <option> elements
selectObject.deselectAll();
  {{< /tab >}}
  {{< tab header="Python" >}}
# Deselect an <option> based upon the <select> element's internal index
select_object.deselect_by_index(1)

# Deselect an <option> based upon its value attribute
select_object.deselect_by_value('value1')

# Deselect an <option> based upon its text
select_object.deselect_by_visible_text('Bread')

# Deselect all selected <option> elements
select_object.deselect_all()
  {{< /tab >}}
  {{< tab header="CSharp" >}}
// Deselect an <option> based upon the <select> element's internal index
selectObject.DeselectByIndex(1);

// Deselect an <option> based upon its value attribute
selectObject.DeselectByValue("value1");

// Deselect an <option> based upon its text
selectObject.DeselectByText("Bread");

// Deselect all selected <option> elements
selectObject.DeselectAll();
  {{< /tab >}}
  {{< tab header="Ruby" >}}
# Deselect an <option> based upon the <select> element's internal index
select_object.deselect_by(:index, 1)

# Deselect an <option> based upon its value attribute
select_object.deselect_by(:value, 'value1')

# Deselect an <option> based upon its text
select_object.deselect_by(:text, 'Bread')

# Deselect all selected <option> elements
select_object.deselect_all
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
// This feature is not implemented - Help us by sending a pr to implement this feature
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
// Deselect an <option> based upon the <select> element's internal index
selectObject.deselectByIndex(1)

// Deselect an <option> based upon its value attribute
selectObject.deselectByValue("value1")

// Deselect an <option> based upon its text
selectObject.deselectByVisibleText("Bread")

// Deselect all selected <option> elements
selectObject.deselectAll()
  {{< /tab >}}
{{< /tabpane >}}

最後に、一部の `<select>` 要素を使用すると、複数のオプションを選択できます。
`<select>` 要素がこれらの1つであるかどうかを調べるには、下記のように記述します。

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
Boolean doesThisAllowMultipleSelections = selectObject.isMultiple();
  {{< /tab >}}
  {{< tab header="Python" >}}
does_this_allow_multiple_selections = select_object.is_multiple
  {{< /tab >}}
  {{< tab header="CSharp" >}}
bool doesThisAllowMultipleSelections = selectObject.IsMultiple;
  {{< /tab >}}
  {{< tab header="Ruby" >}}
does_this_allow_multiple_selections = select_object.multiple?
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
// This feature is not implemented - Help us by sending a pr to implement this feature
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
val doesThisAllowMultipleSelections = selectObject.isMultiple
  {{< /tab >}}
{{< /tabpane >}}