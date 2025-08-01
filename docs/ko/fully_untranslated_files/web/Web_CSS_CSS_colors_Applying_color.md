---
title: CSS로 HTML 요소에 색 입히기
slug: Web/CSS/CSS_colors/Applying_color
---

{{HTMLSidebar}}

색은 인간의 감정을 표현하는 기본적인 형태입니다. 아이들은 뭔가 그릴 수 있는 민첩성을 갖추기도 전에 색을 가지고 놉니다. 사람들이 웹 사이트를 개발할 때 보통 색을 제일 먼저 입혀보고 싶어 하는 건 이런 이유일지도 모릅니다. [CSS](/ko/docs/Web/CSS)와 함께라면 무궁무진한 방법으로 여러분의 [HTML](/ko/docs/Web/HTML) [요소](/ko/docs/Web/HTML/Element)에 색을 넣어 원하는 모습을 만들 수 있습니다. 이 글은 CSS 색을 HTML에 적용하는 기초를 소개합니다.

다행히도 HTML에 색을 추가하는 건 정말 쉽고 거의 모든 곳에 할 수 있는 일입니다.

[색을 입힐 수 있는 목록, 그때 사용할 CSS 속성](#색을_입힐_수_있는_것), [색을 나타내는 법](#색을_나타내는_법), [실제로 색 사용하기](#색_사용하기) 등 색을 쓸 때 알아야 할 주제는 대부분 짚고 가겠습니다. [사용자가 색을 선택](#사용자의_색_선택)할 수 있는 방법도 확인해보겠습니다.

마지막으로는 적절한 색을 고르고, 서로 다른 시각적 조건을 가진 사람들을 고려하는 등 [현명한 색 선택](#현명하게_색_고르기)에 대해 간단히 알아보겠습니다.

## 색을 입힐 수 있는 것

요소 차원에서 보자면 HTML의 모든 것에 색을 입힐 수 있습니다. 대신에 글씨와 테두리처럼, 요소 안에 그려지는 것의 종류에 따라 알아보겠습니다. 각각의 종류에 적용할 수 있는 CSS 속성의 목록도 보겠습니다.

가장 기초적인 단계로는 {{cssxref("color")}} 속성이 HTML 요소의 콘텐츠 전경색을 지정하고, {{cssxref("background-color")}} 속성이 요소의 배경색을 지정합니다. 두 속성은 거의 모든 요소에 사용할 수 있습니다.

### 글씨

요소를 렌더링할 때 글씨, 글씨 배경과 기타 꾸미기 효과의 색은 아래에 나열한 속성이 결정합니다.

- {{cssxref("color")}}
  - : 글씨와 글씨 장식(밑줄, 윗줄, 취소선 등)을 그릴 때 사용할 색입니다.
- {{cssxref("background-color")}}
  - : 글씨의 배경색입니다.
- {{cssxref("text-shadow")}}
  - : 글씨의 그림자 효과를 설정합니다. 여러 옵션 중에서 그림자 색을 정할 수 있습니다. (이후 다른 옵션에 따라 흐려지고 배경과 섞입니다)

    See [Text drop shadows](/ko/docs/Learn/CSS/Styling_text/Fundamentals#text_drop_shadows) to learn more.

- {{cssxref("text-decoration-color")}}
  - : 기본 설정에서 글씨 장식(밑줄, 윗줄, 취소선 등)은 `color` 속성의 값을 색으로 사용합니다. 그러나 `text-decoration-color` 속성을 지정하면 다른 색으로 바꿀 수 있습니다.
- {{cssxref("text-emphasis-color")}}
  - : 글씨 위에 표시할 강조 표시의 색입니다.
- {{cssxref("caret-color")}}
  - : 요소의 {{Glossary("caret", "캐럿")}}(글씨 입력 커서) 색입니다. {{HTMLElement("input")}}이나 {{HTMLElement("textarea")}}, HTML [`contenteditable`](/ko/docs/Web/HTML/Global_attributes#contenteditable) 속성을 설정한 요소처럼 편집 가능한 경우에만 유용합니다.

### 박스

모든 요소는 모종의 콘텐츠를 가진 박스로, 콘텐츠 외에도 배경과 테두리를 가질 수 있습니다.

- [테두리](#테두리)
  - [: 테두리](#테두리) 항목에서 박스 테두리에 사용할 수 있는 CSS 속성의 목록을 확인하세요.
- {{cssxref("background-color")}}
  - : 전경 콘텐츠가 없는 곳에 표시할 배경색입니다.
- {{cssxref("column-rule-color")}}
  - : 긴 글씨를 여러 단으로 나눌 때 그릴 구분선의 색입니다.
- {{cssxref("outline-color")}}
  - : 요소의 바깥에 외곽선을 그릴 때 사용할 색입니다. 외곽선은 문서에서 공간을 차지하지 않아서 다른 요소를 가릴 수 있다는 점에서 테두리와 다릅니다. 보통 현재 선택돼 입력 이벤트를 받을 수 있는 요소를 강조할 때 사용합니다.

### 테두리

모든 요소는 주위에 테두리를 가질 수 있습니다. 기본적인 테두리는 요소 콘텐츠의 모서리를 따라 그리는 선입니다. See [Box properties](/ko/docs/Learn/CSS/Introduction_to_CSS/Box_model#box_properties) to learn about the relationship between elements and their borders, and the article [Styling borders using CSS](/ko/docs/Learn/CSS/Building_blocks/Backgrounds_and_borders) to learn more about applying styles to borders.

{{cssxref("border")}} 단축 속성을 사용하면 색은 물론 [너비](/ko/docs/Web/CSS/border-width)와 [스타일](/ko/docs/Web/CSS/border-style)(실선, 점선 등)같은 속성을 한 번에 설정할 수 있습니다.

- {{cssxref("border-color")}}
  - : 모든 면의 테두리가 사용할 단색입니다.
- {{cssxref("border-left-color")}}, {{cssxref("border-right-color")}}, {{cssxref("border-top-color")}}, {{cssxref("border-bottom-color")}}
  - : 테두리 색을 방향에 따라 다르게 설정할 수 있습니다.
- {{cssxref("border-block-start-color")}}, {{cssxref("border-block-end-color")}}
  - : With these, you can set the color used to draw the borders which are closest to the start and end of the block the border surrounds. In a left-to-right writing mode (such as the way English is written), the block start border is the top edge and the block end is the bottom. This differs from the inline start and end, which are the left and right edges (corresponding to where each line of text in the box begins and ends).
- {{cssxref("border-inline-start-color")}}, {{cssxref("border-inline-end-color")}}
  - : These let you color the edges of the border closest to to the beginning and the end of the start of lines of text within the box. Which side this is will vary depending on the {{cssxref("writing-mode")}}, {{cssxref("direction")}}, and {{cssxref("text-orientation")}} properties, which are typically (but not always) used to adjust text directionality based on the language being displayed. For example, if the box's text is being rendered right-to-left, then the `border-inline-start-color` is applied to the right side of the border.

### 다른 방법

웹 기술에서 CSS만 색을 지원하는건 아닙니다. 웹에서 사용할 수 있는 다른 그래픽 기술에서도 색을 지원합니다.

- HTML [Canvas API](/ko/docs/Web/API/Canvas_API)
  - : {{HTMLElement("canvas")}} 요소로 2D 비트맵 그래픽을 그릴 수 있습니다. [캔버스 자습서](/ko/docs/Web/API/Canvas_API/Tutorial)를 방문해 더 알아보세요.
- [SVG](/ko/docs/Web/SVG) (Scalable Vector Graphics)
  - : 선, 패턴, 특정 모양의 형태를 그리는 명령어를 사용해 이미지를 그릴 수 있습니다. SVG 명령어는 XML 형식을 따르며, 웹 페이지에 바로 삽입할 수도 있고, 다른 이미지처럼 {{HTMLElement("img")}} 요소에 넣을 수도 있습니다.
- [WebGL](/ko/docs/Web/API/WebGL_API)
  - : Web Graphics Library는 OpenGL ES 기반의 API로, 웹에서 고성능 2D 및 3D 그래픽을 그릴 수 있습니다. [WebGL 자습서](/ko/docs/Web/API/WebGL_API/Tutorial/Getting_started_with_WebGL)를 방문해 더 알아보세요.

## 색을 나타내는 법

CSS에서 색을 나타내려면 우선 "색"이라는 개념을, 원색이나 밝기 등 구성 요소를 분리해 수치로 표기하는 등 컴퓨터가 이해할 수 있는 디지털 형태로 변환해야 합니다. 변환 방법이 여러 가지이듯 CSS가 색을 표현하는 방법도 여러 가지입니다.

각각의 형태에 대한 더 자세한 내용은 CSS {{cssxref("&lt;color&gt;")}} 단위 문서를 참고하세요.

### 키워드

CSS 표준은 다수의 색 키워드를 사전에 정의하고 있으므로, 원하는 색을 가리키는 키워드가 있다면 숫자형 표현 대신 사용할 수 있습니다. 색 키워드는 원색과 2차색(`red`, `blue`, `orange` 등), 단계별 무채색(`black`에서 `white`까지, `darkgray`와 `lightgrey` 등) 외에도 `lightseagreen`, `cornflowerblue`, `rebeccapurple`처럼 다양한 종류의 혼합색을 포함하고 있습니다.

사용할 수 있는 모든 색 키워드의 목록은 [`<color>`의 색상 키워드 항목](/ko/docs/Web/CSS/color_value#%EC%83%89%EC%83%81_%ED%82%A4%EC%9B%8C%EB%93%9C)을 참고하세요.

### RGB 값

RGB 색은 세 가지 방법으로 표현할 수 있습니다.

#### 16진수 문자열 표기법

16진수 문자열 표기법은 색의 구성요소(빨강, 초록, 파랑)를 16진수 숫자로 표현합니다. 네 번째 구성 요소로 알파 채널(불투명도)을 포함할 수도 있습니다. 하나의 구성 요소는 0에서 255 사이(0x00에서 0xFF)를 숫자 두 개로, 또는 0에서 15 사이(0x0에서 0xF)를 숫자 한 개로 표기합니다. 단, 모든 구성 요소는 같은 수의 문자로 표기해야 합니다. 한 자릿수(0\~F)로 표기한다면, 구성 요소의 최종 값은 자신의 문자를 두 번씩 사용해 계산합니다. 즉, `"#D"`의 값은 `"#DD"`입니다.

16진수 문자열 표기법은 항상 `"#"`으로 시작해야 하고, 16진수 숫자는 그 후에 위치합니다. 문자열은 대소문자를 구분하지 않습니다.

- `"#rrggbb"`
  - : 완전히 불투명한 색을 지정합니다. 구성 요소 중 빨강은 16진수 `0xrr`, 초록은 `0xgg`, 파랑은 `0xbb`입니다.
- `"#rrggbbaa"`
  - : 구성 요소 중 빨강은 16진수 `0xrr`, 초록은 `0xgg`, 파랑은 `0xbb`인 색을 지정합니다. 알파 채널의 값은 `0xaa`로, 값이 낮을 수록 색은 더 투명해집니다.
- `"#rgb"`
  - : 완전히 불투명한 색을 지정합니다. 구성 요소 중 빨강은 16진수 `0xrr`, 초록은 `0xgg`, 파랑은 `0xbb`입니다.
- `"#rgba"`
  - : 구성 요소 중 빨강은 16진수 `0xrr`, 초록은 `0xgg`, 파랑은 `0xbb`인 색을 지정합니다. 알파 채널의 값은 `0xaa`로, 값이 낮을 수록 색은 더 투명해집니다.

예를 하나 들자면 불투명한 파랑은 `"#0000ff"`이나 `"#00f"`로 표현할 수 있습니다. 25%만 불투명한 파랑으로 만들 땐 `"#0000ff44"` 또는 `"#00f4"`로 표기합니다.

#### RGB 함수형 표기법

16진수 문자열 표기법과 같이, RGB(Red/Green/Blue) 함수 표기법은 빨강, 초록, 파랑, 그리고 불투명도를 나타낼 선택적 알파 채널 구성요소를 사용해 색을 나타냅니다. 그러나 문자열 표기법과 달리 CSS 함수 {{cssxref("color_value", "rgb()", "#rgb()")}}를 사용합니다. `rgb()` 함수의 세 매개변수는 순서대로 빨강, 파랑, 초록 값이며, 생략 가능한 마지막 네 번째 매개변수가 알파 채널을 나타냅니다.

각 매개변수의 유효한 값은 다음과 같습니다.

- `red`, `green`, `blue`
  - : 각각 0 이상, 255 이하인 {{cssxref("&lt;integer&gt;")}}이거나, 또는 0% 이상 100% 이하인 {{cssxref("&lt;percentage&gt;")}}여야 합니다.
- `alpha`
  - : 0.0(완전히 투명) 이상, 1.0(완전히 불투명) 이하의 숫자여야 합니다. 백분율도 사용할 수 있으며, 0%는 0.0, 100%는 1.0에 대응합니다.

예를 들어, 50% 불투명도의 밝은 빨강은 `rgb(255, 0, 0, 0.5)`와 `rgb(100%, 0, 0, 50%)` 두 방법으로 만들 수 있습니다.

### HSL 함수형 표기법

많은 경우, 디자이너와 아티스트는 HSL(색조/채도/명도) 모델을 사용한 색을 선호합니다. 웹에서 HSL 색상은 HSL 함수 표기법을 사용해 나타냅니다. CSS `hsl()` 함수의 사용법 자체는 `rgb()` 함수와 매우 유사합니다.

The diagram below shows an HSL color cylinder. Hue defines the actual color based on the position along a circular {{glossary("color wheel")}} representing the colors of the visible spectrum. Saturation is a percentage of how much of the way between being a shade of gray and having the maximum possible amount of the given hue. As the value of luminance (or lightness) increases, the color transitions from the darkest possible to the brightest possible (from black to white). Image courtesy of user [SharkD](https://commons.wikimedia.org/wiki/User:SharkD) on [Wikipedia](https://www.wikipedia.org/), distributed under the [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) license.

![HSL color cylinder](640px-hsl_color_solid_cylinder.png)

The value of the hue (H) component of an HSL color is an angle from red around through yellow, green, cyan, blue, and magenta (ending up back at red again at 360°) that identifies what the base color is. The value can be specified in any {{cssxref("&lt;angle&gt;")}} unit supported by CSS, including degrees (`deg`), radians (`rad`), gradians (`grad`), or turns (`turn`). But this doesn't control how vivid or dull, or how bright or dark the color is.

The saturation (S) component of the color specifies what percentage of the final color is comprised of the specified hue. The rest is defined by the grey level provided by the luminance (L) component.

Think of it like creating the perfect paint color:

1. You start with base paint that's the maximum intensity possible for a given color, such as the most intense blue that can be represented by the user's screen. This is the **hue** (H) component: a value representing the angle around the {{glossary("color wheel")}} for the vivid hue we want to use as our base.
2. Then select a greyscale paint that corresponds how bright you want the color to be; this is the luminance. Do you want it to be very bright and nearly white, or very dark and closer to black, or somewhere in between? This is specified using a percentage, where 0% is perfectly black and 100% is perfectly white (regardless of the saturation or hue). In between values are a literal grey area.
3. Now that you have a grey paint and a perfectly vivid color, you need to mix them together. The saturation (S) component of the color indicates what percentage of the final color should be comprised of that perfectly vivid color. The rest of the final color is made up of the grey paint that represents the saturation.

You can also optionally include an alpha channel, to make the color less than 100% opaque.

Here are some sample colors in HSL notation:

```css hidden
table {
  border: 1px solid black;
  font:
    16px "Open Sans",
    Helvetica,
    Arial,
    sans-serif;
  border-spacing: 0;
  border-collapse: collapse;
}

th,
td {
  border: 1px solid black;
  padding: 4px 6px;
  text-align: left;
}

th {
  background-color: hsl(0, 0%, 75%);
}
```

```html
<table>
  <thead>
    <tr>
      <th scope="col">Color in HSL notation</th>
      <th scope="col">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>hsl(90deg, 100%, 50%)</code></td>
      <td style="background-color: hsl(90deg, 100%, 50%);">&nbsp;</td>
    </tr>
    <tr>
      <td><code>hsl(90, 100%, 50%)</code></td>
      <td style="background-color: hsl(90, 100%, 50%);">&nbsp;</td>
    </tr>
    <tr>
      <td><code>hsl(0.15turn, 50%, 75%)</code></td>
      <td style="background-color: hsl(0.15turn, 50%, 75%);">&nbsp;</td>
    </tr>
    <tr>
      <td><code>hsl(0.15turn, 90%, 75%)</code></td>
      <td style="background-color: hsl(0.15turn, 90%, 75%);">&nbsp;</td>
    </tr>
    <tr>
      <td><code>hsl(0.15turn, 90%, 50%)</code></td>
      <td style="background-color: hsl(0.15turn, 90%, 50%);">&nbsp;</td>
    </tr>
    <tr>
      <td><code>hsl(270deg, 90%, 50%)</code></td>
      <td style="background-color: hsl(270deg, 90%, 50%);">&nbsp;</td>
    </tr>
  </tbody>
</table>
```

{{EmbedLiveSample("HSL_functional_notation", 300, 260)}}

> **Note:** When you omit the hue's unit, it's assumed to be in degrees (`deg`).

### HWB functional notation

Much like the HSL functional notation above, the [hwb()](/ko/docs/Web/CSS/color_value/hwb) function uses the same hue value. But instead of lightness and saturation you specify whiteness and blackness values in percentages. Values are **not** separated with a comma and an optional alpha value can be included (it must be preceded by a forward slash `/`).

Here are some examples of using HWB notation:

```css
/* These examples all specify varying shades of a lime green. */
hwb(90 10% 10%)
hwb(90 10% 10%)
hwb(90 50% 10%)
hwb(90deg 10% 10%)
hwb(1.5708rad 60% 0%)
hwb(.25turn 0% 40%)

/* Same lime green but with an alpha value */
hwb(90 10% 10% / 0.5)
hwb(90 10% 10% / 50%)
```

## Using color

Now that you know what CSS properties exist that let you apply color to elements and the formats you can use to describe colors, you can put this together to begin to make use of color. As you may have seen from the list under [Things that can have color](#things_that_can_have_color), there are plenty of things you can color with CSS. Let's look at this from two sides: using color within a {{Glossary("stylesheet")}}, and adding and changing color using {{Glossary("JavaScript")}} code to alter the styles of elements.

### Specifying colors in stylesheets

The easiest way to apply color to elements—and the way you'll usually do it—is to specify colors in the CSS that's used when rendering elements. While we won't use every single property mentioned previously, we'll look at a couple of examples. The concept is the same anywhere you use color.

Let's take a look at an example, starting by looking at the results we're trying to achieve:

{{EmbedLiveSample("Specifying_colors_in_stylesheets", 650, 150)}}

#### HTML

The HTML responsible for creating the above example is shown here:

```html
<div class="wrapper">
  <div class="box boxLeft">
    <p>This is the first box.</p>
  </div>
  <div class="box boxRight">
    <p>This is the second box.</p>
  </div>
</div>
```

This is pretty simple, using a {{HTMLElement("div")}} as a wrapper around the contents, which consists of two more `<div>`s, each styled differently with a single paragraph ({{HTMLElement("p")}}) in each box.

The magic happens, as usual, in the CSS, where we'll apply colors define the layout for the HTML above.

#### CSS

We'll look at the CSS to create the above results a piece at a time, so we can review the interesting parts one by one.

```css
.wrapper {
  width: 620px;
  height: 110px;
  margin: 0;
  padding: 10px;
  border: 6px solid mediumturquoise;
}
```

The `.wrapper` class is used to assign styles to the {{HTMLElement("div")}} that encloses all of our other content. This establishes the size of the container using {{cssxref("width")}} and {{cssxref("height")}} as well as its {{cssxref("margin")}} and {{cssxref("padding")}}.

Of more interest to our discussion here is the use of the {{cssxref("border")}} property to establish a border around the outside edge of the element. This border is a solid line, 6 pixels wide, in the color `mediumturquoise`.

Our two colored boxes share a number of properties in common, so next we establish a class, `.box`, that defines those shared properties:

```css
.box {
  width: 290px;
  height: 100px;
  margin: 0;
  padding: 4px 6px;
  font:
    28px "Marker Felt",
    "Zapfino",
    cursive;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

In brief, `.box` establishes the size of each box, as well as the configuration of the font used within. We also take advantage of [CSS Flexbox](/ko/docs/Web/CSS/CSS_Flexible_Box_Layout) to easily center the contents of each box. We enable `flex` mode using {{cssxref("display", "display: flex")}}, and set both {{cssxref("justify-content")}} and {{cssxref("align-items")}} to `center`. Then we can create a class for each of the two boxes that defines the properties that differ between the two.

```css
.boxLeft {
  float: left;
  background-color: rgb(245, 130, 130);
  outline: 2px solid darkred;
}
```

The `.boxLeft` class—which, cleverly, is used to style the box on the left—floats the box to the left, then sets up the colors:

- The box's background color is set by changing the value of the CSS {{cssxref("background-color")}} property to `rgb(245, 130, 130)`.
- An outline is defined for the box. Unlike the more commonly used `border`, {{cssxref("outline")}} doesn't affect layout at all; it draws over the top of whatever may happen to be outside the element's box instead of making room as `border` does. This outline is a solid, dark red line that's two pixels thick. Note the use of the `darkred` keyword when specifying the color.
- Notice that we're not explicitly setting the text color. That means the value of {{cssxref("color")}} will be inherited from the nearest containing element that defines it. By default, that's black.

```css
.boxRight {
  float: right;
  background-color: hsl(270deg, 50%, 75%);
  outline: 4px dashed rgb(110, 20, 120);
  color: hsl(0deg, 100%, 100%);
  text-decoration: underline wavy #88ff88;
  text-shadow: 2px 2px 3px black;
}
```

> **Note:** When you try to show it in Safari, it will not show properly. Because Safari doesn't support `text-decoration: underline wavy #88ff88`.

Finally, the `.boxRight` class describes the unique properties of the box that's drawn on the right. It's configured to float the box to the right so that it appears next to the previous box. Then the following colors are established:

- The `background-color` is set using the HSL value specified using `hsl(270deg, 50%, 75%)`. This is a medium purple color.
- The box's `outline` is used to specify that the box should be enclosed in a four pixel thick dashed line whose color is a somewhat deeper purple (`rgb(110, 20, 120)`).
- The foreground (text) color is specified by setting the {{cssxref("color")}} property to `hsl(0deg, 100%, 100%)`. This is one of many ways to specify the color white.
- We add a green wavy line under the text with {{cssxref("text-decoration")}}.
- Finally, a bit of a shadow is added to the text using {{cssxref("text-shadow")}}. Its `color` parameter is set to `black`.

## Letting the user pick a color

There are many situations in which your website may need to let the user select a color. Perhaps you have a customizable user interface, or you're implementing a drawing app. Maybe you have editable text and need to let the user choose the text color. Or perhaps your app lets the user assign colors to folders or items. Although historically it's been necessary to implement your own [color picker](https://en.wikipedia.org/wiki/Color_picker), HTML now provides support for browsers to provide one for your use through the {{HTMLElement("input")}} element, by using `"color"` as the value of its [`type`](/ko/docs/Web/HTML/Element/input#type) attribute.

The `<input>` element represents a color only in the [hexadecimal string notation](#hexadecimal_string_notation) covered above.

### Example: Picking a color

Let's look at a simple example, in which the user can choose a color. As the user adjusts the color, the border around the example changes to reflect the new color. After finishing up and picking the final color, the color picker's value is displayed.

{{EmbedLiveSample("Example_Picking_a_color", 525, 275)}}

> **Note:** On macOS, you indicate that you've finalized selection of the color by closing the color picker window.

#### HTML

The HTML here creates a box that contains a color picker control (with a label created using the {{HTMLElement("label")}} element) and an empty paragraph element ({{HTMLElement("p")}}) into which we'll output some text from our JavaScript code.

```html
<div id="box">
  <label for="colorPicker">Border color:</label>
  <input type="color" value="#8888ff" id="colorPicker" />
  <p id="output"></p>
</div>
```

#### CSS

The CSS establishes a size for the box and some basic styling for appearances. The border is also established with a 2-pixel width and a border color.

```css
#box {
  width: 500px;
  height: 200px;
  border: 2px solid rgb(245, 220, 225);
  padding: 4px 6px;
  font:
    16px "Lucida Grande",
    "Helvetica",
    "Arial",
    "sans-serif";
}
```

#### JavaScript

The script here handles the task of updating the starting color of the border to match the color picker's value. Then two event handlers are added to deal with input from the [`<input type="color">`](/ko/docs/Web/HTML/Element/input/color) element.

```js
const colorPicker = document.getElementById("colorPicker");
const box = document.getElementById("box");
const output = document.getElementById("output");

box.style.borderColor = colorPicker.value;

colorPicker.addEventListener(
  "input",
  (event) => {
    box.style.borderColor = event.target.value;
  },
  false,
);

colorPicker.addEventListener(
  "change",
  (event) => {
    output.innerText = `Color set to ${colorPicker.value}.`;
  },
  false,
);
```

The {{domxref("HTMLElement/input_event", "input")}} event is sent every time the value of the element changes; that is, every time the user adjusts the color in the color picker. Each time this event arrives, we set the box's border color to match the color picker's current value.

The {{domxref("HTMLElement/change_event", "change")}} event is received when the color picker's value is finalized. We respond by setting the contents of the `<p>` element with the ID `"output"` to a string describing the finally selected color.

## Using color wisely

Making the right choices when selecting colors when designing a website can be a tricky process, especially if you aren't well-grounded in art, design, or at least basic color theory. The wrong color choice can render your site unattractive, or even worse, leave the content unreadable due to problems with contrast or conflicting colors. Worse still, if using the wrong colors can result in your content being outright unusable by people with certain vision problems, particularly color blindness.

### Finding the right colors

Coming up with just the right colors can be tricky, especially without training in art or design. Fortunately, there are tools available that can help you. While they can't replace having a good designer helping you make these decisions, they can definitely get you started.

#### Base color

The first step is to choose your **base color**. This is the color that in some way defines your website or the subject matter of the site. Just as we associate green with the beverage [Mountain Dew](https://en.wikipedia.org/wiki/Mountain_Dew) and one might think of the color blue in relationship with the sky or the ocean, choosing an appropriate base color to represent your site is a good place to start. There are plenty of ways to select a base color; a few ideas include:

- A color that is naturally associated with the topic of your content, such as the existing color identified with a product or idea or a color representative of the emotion you wish to convey.
- A color that comes from imagery associated with what your content is about. If you're creating a website about a given item or product, choose a color that's physically present on that item.
- Browse websites that let you look at lots of existing color palettes and images to find inspiration.

When trying to decide upon a base color, you may find that browser extensions that let you select colors from web content can be particularly handy. Some of these are even specifically designed to help with this sort of work. For example, the website [ColorZilla](https://www.colorzilla.com/) offers an extension ([Chrome](https://www.colorzilla.com/chrome/) / [Firefox](https://www.colorzilla.com/firefox/)) that offers an eyedropper tool for picking colors from the web. It can also take averages of the colors of pixels in various sized areas or even a selected area of the page.

> **Note:** The advantage to averaging colors can be that often what looks like a solid color is actually a surprisingly varied number of related colors all used in concert, blending to create a desired effect. Picking just one of these pixels can result in getting a color that on its own looks very out of place.

#### Fleshing out the palette

Once you have decided on your base color, there are plenty of online tools that can help you build out a palette of appropriate colors to use along with your base color by applying color theory to your base color to determine appropriate added colors. Many of these tools also support viewing the colors filtered so you can see what they would look like to people with various forms of color blindness. See [Color and accessibility](#color_and_accessibility) for a brief explanation of why this matters.

A few examples (all free to use as of the time this list was last revised):

- [MDN's color picker tool](/ko/docs/Web/CSS/CSS_Colors/Color_picker_tool)
- [Paletton](https://paletton.com/)
- [Adobe Color CC online color wheel](https://color.adobe.com/create/color-wheel)

When designing your palette, be sure to keep in mind that in addition to the colors these tools typically generate, you'll probably also need to add some core neutral colors such as white (or nearly white), black (or nearly black), and some number of shades of gray.

> **Note:** Usually, you are far better off using the smallest number of colors possible. By using color to accentuate rather than adding color to everything on the page, you keep your content easy to read and the colors you do use have far more impact.

### Color theory resources

A full review of color theory is beyond the scope of this article, but there are plenty of articles about color theory available, as well as courses you can find at nearby schools and universities. A couple of useful resources about color theory:

- [Color Science](https://www.khanacademy.org/computing/pixar/color) ([Khan Academy](https://www.khanacademy.org/) in association with [Pixar](https://www.pixar.com/))
  - : An online course which introduces concepts such as what color is, how it's perceived, and how to use colors to express ideas. Presented by Pixar artists and designers.
- [Color theory](https://en.wikipedia.org/wiki/Color_theory) on Wikipedia
  - : Wikipedia's entry on color theory, which has a lot of great information from a technical perspective. It's not really a resource for helping you with the color selection process, but is still full of useful information.

### Color and accessibility

There are several ways color can be an {{Glossary("accessibility")}} problem. Improper or careless use of color can result in a website or app that a percentage of your target audience may not be able to use adequately, resulting in lost traffic, lost business, and possibly even a public relations problem. So it's important to consider your use of color carefully.

You should do at least basic research into [color blindness](https://en.wikipedia.org/wiki/Color_blindness). There are several kinds; the most common is red-green color blindness, which causes people to be unable to differentiate between the colors red and green. There are others, too, ranging from inabilities to tell the difference between certain colors to total inability to see color at all.

> **Note:** The most important rule: never use color as the only way to know something. If, for example, you indicate success or failure of an operation by changing the color of a shape from white to green for success and red for failure, users with red-green color-blindness won't be able to use your site properly. Instead, perhaps use both text and color together, so that everyone can understand what's happening.

For more information about color blindness, see the following articles:

- [Medline Plus: Color Blindness](https://medlineplus.gov/colorblindness.html) (United States National Institute of Health)
- [American Academy of Ophthalmology: What Is Color Blindness?](https://www.aao.org/eye-health/diseases/what-is-color-blindness)
- [Color Blindness & Web Design](https://www.usability.gov/get-involved/blog/2010/02/color-blindness.html) (Usability.gov: United States Department of Health and Human Services)

### Palette design example

Let's consider a quick example of selecting an appropriate color palette for a site. Imagine that you're building a website for a new game that takes place on the planet Mars. So let's do a [Google search for photos of Mars](https://www.google.com/search?q=Mars&tbm=isch). Lots of good examples of Martian coloration there. We carefully avoid the mockups and the photos from movies. And we decide to use a photo taken by one of the Mars landers humanity has parked on the surface over the last few decades, since the game takes place on the planet's surface. We use a color picker tool to select a sample of the color we choose.

Using an eyedropper tool, we identify a color we like and determine that the color in question is `#D79C7A`, which is an appropriate rusty orange-red color that's so stereotypical of the Martian surface.

Having selected our base color, we need to build out our palette. We decide to use [Paletton](https://www.paletton.com/) to come up with the other colors we need. Upon opening Paletton, we see:

![Right after loading Paletton.](paletton1.png)

Next, we enter our color's hex code (`D79C7A`) into the "Base RGB" box at the bottom-left corner of the tool:

![After entering base color](paletton2.png)

We now see a monochromatic palette based on the color we picked from the Mars photo. If you need a lot of related colors for some reason, those are likely to be good ones. But what we really want is an accent color. Something that will pop along side the base color. To find that, we click the "add complementary" toggle underneath the menu that lets you select the palette type (currently "Monochromatic"). Paletton computes an appropriate accent color; clicking on the accent color down in the bottom-right corner tells us that this color is `#508D7C`.

![Now with complementary colors included.](paletton3.png)

If you're unhappy with the color that's proposed to you, you can change the color scheme, to see if you find something you like better. For example, if we don't like the proposed greenish-blue color, we can click the Triad color scheme icon, which presents us with the following:

![Triad color scheme selected](paletton4.png)

That greyish blue in the top-right looks pretty good. Clicking on it, we find that it's `#556E8D`. That would be used as the accent color, to be used sparingly to make things stand out, such as in headlines or in the highlighting of tabs or other indicators on the site:

![Triad color scheme selected](paletton-color-detail.png)

Now we have our base color and our accent. On top of that, we have a few complementary shades of each, just in case we need them for gradients and the like. The colors can then be exported in a number of formats so you can make use of them.

Once you have these colors, you will probably still need to select appropriate neutral colors. Common design practice is to try to find the sweet spot where there's just enough contrast that the text is crisp and readable but not enough contrast to become harsh for the eyes. It's easy to go too far in one way or another so be sure to get feedback on your colors once you've selected them and have examples of them in use available. If the contrast is too low, your text will tend to be washed out by the background, leaving it unreadable, but if your contrast is too high, the user may find your site garish and unpleasant to look at.

### Color, backgrounds, contrast, and printing

What looks good on screen may look very different on paper.
In addition, ink can be expensive, and if a user is printing your page, they don't necessarily need all the backgrounds and such using up their precious ink when all that matters is the text itself.
Most browsers, by default, remove background images when printing documents.

If your background colors and images have been selected carefully and/or are crucial to the usefulness of the content, you can use the CSS {{cssxref("print-color-adjust")}} property to tell the browser that it should not make adjustments to the appearance of content.

The default value of `print-color-adjust`, `economy`, indicates that the browser is allowed to make appearance changes as it deems necessary in order to try to optimize the legibility and/or print economy of the content, given the type of output device the document is being drawn onto.

You can set `print-color-adjust` to `exact` to tell the browser that the element or elements on which you use it have been designed specifically to best work with the colors and images left as they are.
With this set, the browser won't tamper with the appearance of the element, and will draw it as indicated by your CSS.

> **Note:** There is no guarantee, though, that `print-color-adjust: exact` will result in your CSS being used exactly as given.
> If the browser provides user preferences to change the output (such as a "don't print backgrounds" checkbox in a print dialog box), that overrides the value of `print-color-adjust`.

## See also

- [Drawing graphics](/ko/docs/Learn/JavaScript/Client-side_web_APIs/Drawing_graphics)
- [Graphics on the web](/ko/docs/Web/Guide/Graphics)
- [MDN's color picker tool](/ko/docs/Web/CSS/CSS_Colors/Color_picker_tool)
