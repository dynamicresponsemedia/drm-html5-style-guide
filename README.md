# ELR HTML5 Style Guide

Adapted from: [http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml#HTML_Style_Rules](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml#HTML_Style_Rules)

### General Formatting Rules
+ Indentation
    + Indent by 4 spaces at a time.
    + Don’t use tabs or mix tabs and spaces for indentation.

            <ul>
                <li>Fantastic
                <li>Great
            </ul>

+ Capitalization
    + Use only lowercase.
    + All code has to be lowercase: This applies to HTML element names, attributes, attribute values (unless text/CDATA), CSS selectors, properties, and property values (with the exception of strings).

            <!-- Not recommended -->
            <A HREF="/">Home</A>
            <!-- Recommended -->
            <img src="google.png" alt="Google">
            /* Not recommended */
            color: #E5E5E5;
            /* Recommended */
            color: #e5e5e5;
    + Do not type any content in all caps
        + this effect is presentational and should not be used in html files
        + use css text-transform to achieve all uppercase style

+ Trailing Whitespace
    + Remove trailing white spaces.
    + Trailing white spaces are unnecessary and can complicate diffs.

            <!-- Not recommended -->
            <p>What?_
            <!-- Recommended -->
            <p>Yes please.

### General Meta Rules
+ Encoding
    + Use UTF-8 (no BOM).
    + Make sure your editor uses UTF-8 as character encoding, without a byte order mark.
    + Specify the encoding in HTML templates and documents via

            <meta charset="utf-8">

    + Do not specify the encoding of style sheets as these assume UTF-8.
    + (More on encodings and when and how to specify them can be found in Handling character encodings in HTML and CSS.)

### Comments
+ Explain code as needed, where possible.
+ Use comments to explain code: What does it cover, what purpose does it serve, why is respective solution used or preferred?
+ (This item is optional as it is not deemed a realistic expectation to always demand fully documented code. Mileage may vary heavily for HTML and CSS code and depends on the project’s complexity.)

### Action Items
+ Mark todos and action items with TODO.
+ Highlight todos by using the keyword TODO only, not other common formats like @@.
+ Append a contact (username or mailing list) in parentheses as with the format TODO(contact).
+ Append action items after a colon as in TODO: action item.

        {# TODO(john.doe): revisit centering #}
        <center>Test</center>
        <!-- TODO: remove optional tags -->
        <ul>
          <li>Apples</li>
          <li>Oranges</li>
        </ul>

### HTML Style Rules
+ Document Type
    + Use HTML5.
    + HTML5 (HTML syntax) is preferred for all HTML documents: <!DOCTYPE html>.
    + (It’s recommended to use HTML, as text/html. Do not use XHTML. XHTML, as application/xhtml+xml, lacks both browser and infrastructure support and offers less room for optimization than HTML.)
    + Although fine with HTML, do not close void elements, i.e. write <br>, not <br />.

### HTML Validity
+ Use valid HTML where possible.
+ Use valid HTML code unless that is not possible due to otherwise unattainable performance goals regarding file size.
+ Use tools such as the W3C HTML validator to test.
+ Using valid HTML is a measurable baseline quality attribute that contributes to learning about technical requirements and constraints, and that ensures proper HTML usage.

        <!-- Not recommended -->
        <title>Test</title>
        <article>This is only a test.

        <!-- Recommended -->
        <!DOCTYPE html>
        <meta charset="utf-8">
        <title>Test</title>
        <article>This is only a test.</article>

### Semantics
+ Use HTML according to its purpose.
+ Use elements (sometimes incorrectly called “tags”) for what they have been created for.
    + For example, use heading elements for headings, p elements for paragraphs, a elements for anchors, etc.
+ Don't use add classes such as .center or .bold for block elements
    + If a block element needs styling add css styles in stylesheets
+ Using HTML according to its purpose is important for accessibility, reuse, and code efficiency reasons.

        <!-- Not recommended -->
        <div onclick="goToRecommendations();">All recommendations</div>

        <!-- Recommended -->
        <a href="recommendations/">All recommendations</a>

+ Headings

    + Always start with h1

    + Headings hierarchy should reset for each section

    + Use css to make headings smaller or larger for presentation

+ Sections and Divs

    + Use sections only when it makes sense sematically

        + Never use a section for presentation

        + Only use sections when a separate sematic section is needed

        + See [http://html5doctor.com/avoiding-common-html5-mistakes/](http://html5doctor.com/avoiding-common-html5-mistakes/)

    + Use divs when they are needed for presentation

        + e.g. wrappers, holders, to visually separate content

### Multimedia Fallback

+ Provide alternative contents for multimedia.

+ For multimedia, such as images, videos, animated objects via canvas, make sure to offer alternative access. For images that means use of meaningful alternative text (alt) and for video and audio transcripts and captions, if available.

+ Providing alternative contents is important for accessibility reasons: A blind user has few cues to tell what an image is about without @alt, and other users may have no way of understanding what video or audio contents are about either.

+ (For images whose alt attributes would introduce redundancy, and for images whose purpose is purely decorative which you cannot immediately use CSS for, use no alternative text, as in alt="".)

        <!-- Not recommended -->
        <img src="spreadsheet.png">
        <!-- Recommended -->
        <img src="spreadsheet.png" alt="Spreadsheet screenshot.">

### Separation of Concerns

+ Separate structure from presentation from behavior.
+ Strictly keep structure (markup), presentation (styling), and behavior (scripting) apart, and try to keep the interaction between the three to an absolute minimum.

+ That is, make sure documents and templates contain only HTML and HTML that is solely serving structural purposes. Move everything presentational into style sheets, and everything behavioral into scripts.

+ In addition, keep the contact area as small as possible by linking as few style sheets and scripts as possible from documents and templates.

+ Separating structure from presentation from behavior is important for maintenance reasons. It is always more expensive to change HTML documents and templates than it is to update style sheets and scripts.

        <!-- Not recommended -->
        <!DOCTYPE html>
        <title>HTML sucks</title>
        <link rel="stylesheet" href="base.css" media="screen">
        <link rel="stylesheet" href="grid.css" media="screen">
        <link rel="stylesheet" href="print.css" media="print">
        <h1 style="font-size: 1em;">HTML sucks</h1>
        <p>I’ve read about this on a few sites but now I’m sure:
          <u>HTML is stupid!!1</u>
        <center>I can’t believe there’s no way to control the styling of
          my website without doing everything all over again!</center>

        <!-- Recommended -->
        <!DOCTYPE html>
        <title>My first CSS-only redesign</title>
        <link rel="stylesheet" href="default.css">
        <h1>My first CSS-only redesign</h1>
        <p>I’ve read about this on a few sites but today I’m actually
          doing it: separating concerns and avoiding anything in the HTML of
          my website that is presentational.
        <p>It’s awesome!

### Entity References

+ Do not use entity references.

+ There is no need to use entity references like &mdash;, &rdquo;, or &#x263a;, assuming the same encoding (UTF-8) is used for files and editors as well as among teams.

+ The only exceptions apply to characters with special meaning in HTML (like < and &) as well as control or “invisible” characters (like no-break spaces).

+ <!-- Not recommended -->
The currency symbol for the Euro is &ldquo;&eur;&rdquo;.

+ <!-- Recommended -->
The currency symbol for the Euro is “€”.

### Optional Tags

+ Always close tags.

        <!-- Not recommended -->
        <!DOCTYPE html>
        <title>Saving money, saving bytes</title>
        <p>Qed.
        <!-- Recommended -->
        <!DOCTYPE html>
        <html>
          <head>
            <title>Spending money, spending bytes</title>
          </head>
          <body>
            <p>Sic.</p>
          </body>
        </html>

### type Attributes

+ Omit type attributes for style sheets and scripts.

+ Do not use type attributes for style sheets (unless not using CSS) and scripts (unless not using JavaScript).

+ Specifying type attributes in these contexts is not necessary as HTML5 implies text/css and text/javascript as defaults. This can be safely done even for older browsers.

        <!-- Not recommended -->
        <link rel="stylesheet" href="//www.google.com/css/maia.css"
          type="text/css">
        <!-- Recommended -->
        <link rel="stylesheet" href="//www.google.com/css/maia.css">
        <!-- Not recommended -->
        <script src="//www.google.com/js/gweb/analytics/autotrack.js"
          type="text/javascript"></script>
        <!-- Recommended -->
        <script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>

### HTML Formatting Rules

+ General Formatting

    + Use a new line for every block, list, or table element, and indent every such child element.

    + Independent of the styling of an element (as CSS allows elements to assume a different role per display property), put every block, list, or table element on a new line.

    + Also, indent them if they are child elements of a block, list, or table element.

    + (If you run into issues around whitespace between list items it’s acceptable to put all li elements in one line. A linter is encouraged to throw a warning instead of an error.)

            <blockquote>
              <p><em>Space</em>, the final frontier.</p>
            </blockquote>
            <ul>
              <li>Moe</li>
              <li>Larry</li>
              <li>Curly</li>
            </ul>
            <table>
              <thead>
                <tr>
                  <th scope="col">Income</th>
                  <th scope="col">Taxes</th>
              <tbody>
                <tr>
                  <td>$ 5.00</td>
                  <td>$ 4.50</td>
            </table>

### HTML Quotation Marks

+ When quoting attributes values, use double quotation marks.

+ Use double ("") rather than single quotation marks ('') around attribute values.

        <!-- Not recommended -->
        <a class='maia-button maia-button-secondary'>Sign in</a>
        <!-- Recommended -->
        <a class="maia-button maia-button-secondary">Sign in</a>

### Buttons and Links

+ Never use a link unless it will have a href attribute. Use a button or div instead.

+ No

        href="#"