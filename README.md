# Blaze for Sitecore - Item Extensions

## About

Blaze Item Extensions - as the name implies - is a set of extensions to the `Sitecore.Data.Items.Item` class that provides helper methods for loading and mapping common Sitecore field types to native C# types or common Sitecore C# types.

* Current version: 0.65
* About & Download: [Sitecore Spark - Blaze - Item Extensions](https://github.com/bmbruno/SitecoreSpark.Blaze.ItemExtensions)

## Requirements

* Sitecore 8.0 or greater

## Getting Started

Include the `SitecoreSpark.Blaze.ItemExtensions.cs` file in your solution and ensure it compiles with the rest of your code.

Use the extensions to help map fields to your POCO models.

For example, take the following component data template in Sitecore:

<TODO: IMG>

Here's the view model in code:

``` csharp
public class PromoViewModel
{
   public string Title { get; set; }

   public string Body { get; set; }

   public DateTime OfferExpires { get; set; }

   public LinkField CallToAction { get; set; s}s
}
```

Here's what your mapping code might look like with _Blaze Item Extensions_:

``` csharp
Item sourceItem = RenderingContext.Current.Rendering.Item;

PromoViewModel viewModel = new PromoViewModel()
{
   Title = sourceItem.GetString("Title"),
   Body = sourceItem.GetString("Body Copy"),
   OfferExpires = sourceItem.GetDateTime("Expires"),
   CallToAction = sourceItem.LoadGeneralLink("Call To Action Link")
};
```

Some methods - such as `GetString()` - can be used for multiple types. The IntelliSense documentation snippets will describe which fields each method can safely load.s

## Contact the Author

For questions / comments / issues, contact me:
* Twitter: [@BrandonMBruno](https://www.twitter.com/BrandonMBruno)
* Email: bmbruno [at] gmail [dot] com
 
## License

MIT License. See accompanying "LICENSE" file.
