# API Reference

## [`chsxf\MFX`](API-Namespace-chsxf_MFX)

### Classes

 - [`ArrayTools`](API-ArrayTools)
 - [`CommandLine`](API-CommandLine)
 - [`Config`](API-Config)
 - [`ConfigConstants`](API-ConfigConstants)
 - [`ConfigManager`](API-ConfigManager)
 - [`CoreManager`](API-CoreManager)
 - [`CoreProfiler`](API-CoreProfiler)
 - [`DataValidator`](API-DataValidator)
 - [`DatabaseConnectionInstance`](API-DatabaseConnectionInstance)
 - [`DatabaseManager`](API-DatabaseManager)
 - [`DatabaseUpdater`](API-DatabaseUpdater)
 - [`ErrorManager`](API-ErrorManager)
 - [`FileTools`](API-FileTools)
 - [`Framework`](API-Framework)
 - [`JSONTools`](API-JSONTools)
 - [`MathTools`](API-MathTools)
 - [`NetworkTools`](API-NetworkTools)
 - [`PaginationManager`](API-PaginationManager)
 - [`RequestResult`](API-RequestResult)
 - [`Scripts`](API-Scripts)
 - [`SessionManager`](API-SessionManager)
 - [`StringTools`](API-StringTools)
 - [`StyleSheets`](API-StyleSheets)
 - [`User`](API-User)
 - [`UserManager`](API-UserManager)
 - [`XMLTools`](API-XMLTools)

### Enums

 - [`HttpStatusCodes`](API-HttpStatusCodes)
 - [`RequestMethod`](API-RequestMethod)
 - [`RequestResultType`](API-RequestResultType)

### Interfaces

 - [`IDatabaseUpdater`](API-IDatabaseUpdater)
 - [`IPaginationProvider`](API-IPaginationProvider)
 - [`IUnfilteredSerializable`](API-IUnfilteredSerializable)


## [`chsxf\MFX\Attributes`](API-Namespace-Attributes)

### Classes

 - [`AbstractRouteAttribute`](API-Attributes-AbstractRouteAttribute)
 - [`AbstractRouteStringAttribute`](API-Attributes-AbstractRouteStringAttribute)
 - [`AnonymousRoute`](API-Attributes-AnonymousRoute)
 - [`ContentType`](API-Attributes-ContentType)
 - [`PostRouteCallback`](API-Attributes-PostRouteCallback)
 - [`PreRouteCallback`](API-Attributes-PreRouteCallback)
 - [`RedirectURL`](API-Attributes-RedirectURL)
 - [`RequiredContentType`](API-Attributes-RequiredContentType)
 - [`RequiredRequestMethod`](API-Attributes-RequiredRequestMethod)
 - [`Route`](API-Attributes-Route)
 - [`Template`](API-Attributes-Template)


## [`chsxf\MFX\DataValidator`](API-Namespace-DataValidator)

### Classes

 - [`AbstractFilter`](API-DataValidator-AbstractFilter)
 - [`AbstractOtherFieldFilter`](API-DataValidator-AbstractOtherFieldFilter)
 - [`DataValidatorException`](API-DataValidator-DataValidatorException)
 - [`Field`](API-DataValidator-Field)
 - [`FieldTypeRegistry`](API-DataValidator-FieldTypeRegistry)

### Enums

 - [`FieldType`](API-DataValidator-FieldType)

### Interfaces

 - [`IMessageDispatcher`](API-DataValidator-IMessageDispatcher)


## [`chsxf\MFX\DataValidator\Fields`](API-Namespace-DataValidator_Fields)

### Classes

 - [`CheckBox`](API-DataValidator\Fields-CheckBox)
 - [`DateTime`](API-DataValidator\Fields-DateTime)
 - [`Email`](API-DataValidator\Fields-Email)
 - [`File`](API-DataValidator\Fields-File)
 - [`Integer`](API-DataValidator\Fields-Integer)
 - [`Password`](API-DataValidator\Fields-Password)
 - [`TextArea`](API-DataValidator\Fields-TextArea)
 - [`WithOptions`](API-DataValidator\Fields-WithOptions)
 - [`Word`](API-DataValidator\Fields-Word)


## [`chsxf\MFX\DataValidator\Filters`](API-Namespace-DataValidator_Filters)

### Classes

 - [`DoNotExistInDB`](API-DataValidator\Filters-DoNotExistInDB)
 - [`ExistsInDB`](API-DataValidator\Filters-ExistsInDB)
 - [`In`](API-DataValidator\Filters-In)
 - [`InFloatRange`](API-DataValidator\Filters-InFloatRange)
 - [`InIntRange`](API-DataValidator\Filters-InIntRange)
 - [`IsOfType`](API-DataValidator\Filters-IsOfType)
 - [`LogicOr`](API-DataValidator\Filters-LogicOr)
 - [`MatchFilter`](API-DataValidator\Filters-MatchFilter)
 - [`Path`](API-DataValidator\Filters-Path)
 - [`RegExp`](API-DataValidator\Filters-RegExp)
 - [`RequiredIfNotEmpty`](API-DataValidator\Filters-RequiredIfNotEmpty)
 - [`Unique`](API-DataValidator\Filters-Unique)


## [`chsxf\MFX\DataValidator\Twig`](API-Namespace-DataValidator_Twig)

### Classes

 - [`DataValidator_FieldGroupNode`](API-DataValidator\Twig-DataValidator_FieldGroupNode)
 - [`DataValidator_FieldGroupTokenParser`](API-DataValidator\Twig-DataValidator_FieldGroupTokenParser)
 - [`DataValidator_FieldNode`](API-DataValidator\Twig-DataValidator_FieldNode)
 - [`DataValidator_FieldTokenParser`](API-DataValidator\Twig-DataValidator_FieldTokenParser)
 - [`DataValidator_ResetCountersToken`](API-DataValidator\Twig-DataValidator_ResetCountersToken)
 - [`DataValidator_ResetCountersTokenParser`](API-DataValidator\Twig-DataValidator_ResetCountersTokenParser)
 - [`Extension`](API-DataValidator\Twig-Extension)


## [`chsxf\MFX\Exceptions`](API-Namespace-Exceptions)

### Classes

 - [`ConfigException`](API-Exceptions-ConfigException)
 - [`MFXException`](API-Exceptions-MFXException)
 - [`ScriptException`](API-Exceptions-ScriptException)
 - [`StyleSheetException`](API-Exceptions-StyleSheetException)


## [`chsxf\MFX\L10n`](API-Namespace-L10n)

### Classes

 - [`Countries`](API-L10n-Countries)
 - [`L10nManager`](API-L10n-L10nManager)
 - [`Languages`](API-L10n-Languages)


## [`chsxf\MFX\Routers`](API-Namespace-Routers)

### Classes

 - [`BaseRouteProvider`](API-Routers-BaseRouteProvider)
 - [`RouteAttributesParser`](API-Routers-RouteAttributesParser)
 - [`RouterData`](API-Routers-RouterData)
 - [`RouterHelpers`](API-Routers-RouterHelpers)

### Interfaces

 - [`IRouteProvider`](API-Routers-IRouteProvider)
 - [`IRouter`](API-Routers-IRouter)


## [`chsxf\MFX\Services`](API-Namespace-Services)

### Interfaces

 - [`IAuthenticationService`](API-Services-IAuthenticationService)
 - [`IConfigService`](API-Services-IConfigService)
 - [`ICoreServiceProvider`](API-Services-ICoreServiceProvider)
 - [`IDatabaseService`](API-Services-IDatabaseService)
 - [`ILocalizationService`](API-Services-ILocalizationService)
 - [`IProfilingService`](API-Services-IProfilingService)
 - [`IRequestService`](API-Services-IRequestService)
 - [`IScriptService`](API-Services-IScriptService)
 - [`ISessionService`](API-Services-ISessionService)
 - [`IStyleSheetService`](API-Services-IStyleSheetService)
 - [`ITemplateService`](API-Services-ITemplateService)


