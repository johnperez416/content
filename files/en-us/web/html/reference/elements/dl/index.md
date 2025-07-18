---
title: "<dl>: The Description List element"
slug: Web/HTML/Reference/Elements/dl
page-type: html-element
browser-compat: html.elements.dl
sidebar: htmlsidebar
---

The **`<dl>`** [HTML](/en-US/docs/Web/HTML) element represents a description list. The element encloses a list of groups of terms (specified using the {{HTMLElement("dt")}} element) and descriptions (provided by {{HTMLElement("dd")}} elements). Common uses for this element are to implement a glossary or to display metadata (a list of key-value pairs).

{{InteractiveExample("HTML Demo: &lt;dl&gt;", "tabbed-standard")}}

```html interactive-example
<p>Cryptids of Cornwall:</p>

<dl>
  <dt>Beast of Bodmin</dt>
  <dd>A large feline inhabiting Bodmin Moor.</dd>

  <dt>Morgawr</dt>
  <dd>A sea serpent.</dd>

  <dt>Owlman</dt>
  <dd>A giant owl-like creature.</dd>
</dl>
```

```css interactive-example
p,
dt {
  font-weight: bold;
}

dl,
dd {
  font-size: 0.9rem;
}

dd {
  margin-bottom: 1em;
}
```

## Attributes

This element also accepts the [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).

- `compact` {{Deprecated_inline}}
  - : This Boolean attribute hints that the list should be rendered in a compact style. The interpretation of this attribute is browser-specific. Use [CSS](/en-US/docs/Web/CSS) instead: to give a similar effect as the `compact` attribute, the CSS property {{cssxref("line-height")}} can be used with a value of `80%`.

## Accessibility

Each screen reader exposes `<dl>` content differently, including total count, terms/definitions context, and navigation methods. These differences are not necessarily bugs.
As of iOS 14, VoiceOver will announce that `<dl>` content is a list when navigating with the virtual cursor (not via the read-all command). VoiceOver does not support list navigation commands with `<dl>`. Be careful applying ARIA `term` and `definition` roles to `<dl>` constructs as VoiceOver (macOS and iOS) will adjust how they are announced.

- [VoiceOver on iOS 14 Supports Description Lists](https://adrianroselli.com/2020/09/voiceover-on-ios-14-supports-description-lists.html)
- [Brief Note on Description List Support](https://adrianroselli.com/2022/12/brief-note-on-description-list-support.html)

## Examples

### Single term and description

```html
<dl>
  <dt>Firefox</dt>
  <dd>
    A free, open source, cross-platform, graphical web browser developed by the
    Mozilla Corporation and hundreds of volunteers.
  </dd>

  <!-- Other terms and descriptions -->
</dl>
```

#### Result

{{EmbedLiveSample("Single_term_and_description")}}

### Multiple terms, single description

```html
<dl>
  <dt>Firefox</dt>
  <dt>Mozilla Firefox</dt>
  <dt>Fx</dt>
  <dd>
    A free, open source, cross-platform, graphical web browser developed by the
    Mozilla Corporation and hundreds of volunteers.
  </dd>

  <!-- Other terms and descriptions -->
</dl>
```

#### Result

{{EmbedLiveSample("Multiple_terms_single_description")}}

### Single term, multiple descriptions

```html
<dl>
  <dt>Firefox</dt>
  <dd>
    A free, open source, cross-platform, graphical web browser developed by the
    Mozilla Corporation and hundreds of volunteers.
  </dd>
  <dd>
    The Red Panda also known as the Lesser Panda, Wah, Bear Cat or Firefox, is a
    mostly herbivorous mammal, slightly larger than a domestic cat (60 cm long).
  </dd>

  <!-- Other terms and descriptions -->
</dl>
```

#### Result

{{EmbedLiveSample("Single_term_multiple_descriptions")}}

### Multiple terms and descriptions

It is also possible to define multiple terms with multiple corresponding descriptions, by combining the examples above.

### Metadata

Description lists are useful for displaying metadata as a list of key-value pairs.

```html
<dl>
  <dt>Name</dt>
  <dd>Godzilla</dd>
  <dt>Born</dt>
  <dd>1952</dd>
  <dt>Birthplace</dt>
  <dd>Japan</dd>
  <dt>Color</dt>
  <dd>Green</dd>
</dl>
```

#### Result

{{EmbedLiveSample('Metadata')}}

Tip: It can be handy to define a key-value separator in the CSS, such as:

```css
dt::after {
  content: ": ";
}
```

### Wrapping name-value groups in `div` elements

HTML allows wrapping each name-value group in a `<dl>` element in a {{HTMLElement("div")}} element. This can be useful when using [microdata](/en-US/docs/Web/HTML/Guides/Microdata), or when [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) apply to a whole group, or for styling purposes.

```html
<dl>
  <div>
    <dt>Name</dt>
    <dd>Godzilla</dd>
  </div>
  <div>
    <dt>Born</dt>
    <dd>1952</dd>
  </div>
  <div>
    <dt>Birthplace</dt>
    <dd>Japan</dd>
  </div>
  <div>
    <dt>Color</dt>
    <dd>Green</dd>
  </div>
</dl>
```

#### Result

{{EmbedLiveSample('Wrapping name-value groups in `div` elements')}}

## Notes

Do not use this element (nor {{HTMLElement("ul")}} elements) to merely create indentation on a page. Although it works, this is a bad practice and obscures the meaning of description lists.

To change the indentation of a description term, use the [CSS](/en-US/docs/Web/CSS) {{cssxref("margin")}} property.

## Technical summary

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >Content categories</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >, and if the <code>&#x3C;dl></code> element's children include one
        name-value group, palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted content</th>
      <td>
        <p>
          Either: Zero or more groups each consisting of one or more
          {{HTMLElement("dt")}} elements followed by one or more
          {{HTMLElement("dd")}} elements, optionally intermixed with
          {{HTMLElement("script")}} and
          {{HTMLElement("template")}} elements.<br />Or: (in
          {{Glossary("WHATWG")}} HTML, {{Glossary("W3C")}} HTML 5.2
          and later) One or more {{HTMLElement("div")}} elements,
          optionally intermixed with {{HTMLElement("script")}} and
          {{HTMLElement("template")}} elements.
        </p>
      </td>
    </tr>
    <tr>
      <th scope="row">Tag omission</th>
      <td>None, both the starting and ending tag are mandatory.</td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>
        Any element that accepts
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >flow content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role"
          >No corresponding role</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role"><code>group</code></a>,
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role"
            >list</a
          ></code
        >, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>{{domxref("HTMLDListElement")}}</td>
    </tr>
  </tbody>
</table>

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{HTMLElement("dt")}}
- {{HTMLElement("dd")}}
