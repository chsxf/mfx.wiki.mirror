Once of the most common features of web pages is pagination. It is also the most boring thing to do (_allegedly_).

MFX provides a way to manage pagination so you don't have to reinvent the wheel each time.

## Pagination Management

In MFX, pagination is handled through the [`PaginationManager`](API-PaginationManager) class and the [`IPaginationProvider`](API-IPaginationProvider) interface.

The interface provides the basic information the pagination manager will need: the total number of items in the paginated collection, and the number of items that should be displayed on each page.

The `PaginationManager` class provides the tools you need to navigate between pages and even set up your SQL queries.

## Initializing Pagination

When entering a paginated route, you have to instantiate the `PaginationManager` class and provides it with an object implementing `IPaginationProvider`. In many cases, the route provider can implement the interface itself, but that's up to you.

When created, the `PaginationManager` instance will try to retrieve pagination data from the current request (it works for most common request methods as MFX uses the `$_REQUEST` global variable).

You can also set up extra parameters if needed. Extra parameters will be propagated betweens requests along with the default parameters. This is useful for things like search filters for example.

## Navigating

The `PaginationManager` class provides all the tools you need to navigate from one page to another. In complement of boolean flags indicating if a previous or next page exists, you can request next and previous page URLs, or basic indices, and more. You can then inject these values in your templates to implement pagination in your views.

The class even provides a SQL limit clause for the current page to add to your queries.
