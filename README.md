# Meet ReverseMarkdown

[![Windows Build status](https://ci.appveyor.com/api/projects/status/xse0bia9olr5shxr?svg=true)](https://ci.appveyor.com/project/BabuAnnamalai/reversemarkdown-net) [![Windows Build status](https://api.travis-ci.org/mysticmind/reversemarkdown-net.svg)](https://travis-ci.org/mysticmind/reversemarkdown-net) [![NuGet Version](http://img.shields.io/nuget/v/ReverseMarkdown.svg?style=flat)](https://www.nuget.org/packages/ReverseMarkdown/)

ReverseMarkdown is a Html to Markdown (http://daringfireball.net/projects/markdown/syntax) converter library in C#. Conversion is very reliable since HtmlAgilityPack (HAP) library is used for traversing the Html DOM.

Note that the library implementation is based on the Ruby based Html to Markdown converter [ xijo/reverse_markdown](https://github.com/xijo/reverse_markdown).

> A new release version is available in nuget which targets .Net 4.5, .Net 4.6 and .Net Standard 1.6

## Usage

You can install the package from NuGet using `Install-Package ReverseMarkdown` or clone the repository and built it yourself. 

```csharp
var converter = new ReverseMarkdown.Converter();

string html = "This a sample <strong>paragraph</strong> from <a href='http://test.com'">my site</a>";

string result = converter.Convert(html);

//result This a sample **paragraph** from [my site](http://test.com)
```

```csharp
// with config
string unknownTags = "pass_through";
bool githubFlavored = true;
var config = new ReverseMarkdown.Config(unknownTags, githubFlavoured);
var converter = new ReverseMarkdown.Converter(config);
```

### UnknownTags config (default pass_through) - how to handle unknown tags. 
Valid options are:
* pass_through - Include the unknown tag completely into the result
* drop - Drop the unknown tag and its content
* bypass - Ignore the unknown tag but try to convert its content
* raise - Raise an error to let you know

## Features
* Supports all the established html tags like h1, h2, h3, h4, h5, h6, p, em, strong, i, b, blockquote, code, img, a, hr, li, ol, ul, table, tr, th, td, br
* Can deal with nested lists

## Copyright

Copyright © 2017 Babu Annamalai

## License

ReverseMarkdown is licensed under [MIT](http://www.opensource.org/licenses/mit-license.php "Read more about the MIT license form"). Refer to [License file](https://github.com/mysticmind/reversemarkdown-net/blob/master/LICENSE) for more information.
