---
title: Prise en charge de la mise en cache pour les services HTTP Web WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 6ce3ceccde01879876960e0288cb600a3a20c204
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279335"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="16bf4-102">Prise en charge de la mise en cache pour les services HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="16bf4-102">Caching Support for WCF Web HTTP Services</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="16bf4-103">vous permet d’utiliser le mécanisme de mise en cache déclaratif déjà disponible dans ASP.NET dans vos services HTTP Web WCF.</span><span class="sxs-lookup"><span data-stu-id="16bf4-103">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="16bf4-104">Il vous permet de mettre en cache les réponses provenant de vos opérations de service HTTP Web WCF.</span><span class="sxs-lookup"><span data-stu-id="16bf4-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="16bf4-105">Lorsqu'un utilisateur envoie un HTTP GET à votre service qui est configuré pour la mise en cache, ASP.NET renvoie la réponse mise en cache et la méthode de service n'est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="16bf4-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="16bf4-106">Lorsque le cache expire, au prochain envoi d'un HTTP GET par un utilisateur, votre méthode de service est appelée et la réponse est encore une fois mise en cache.</span><span class="sxs-lookup"><span data-stu-id="16bf4-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="16bf4-107">Pour plus d’informations sur la mise en cache ASP.NET, consultez [vue d’ensemble de la mise en cache ASP.net](/previous-versions/aspnet/ms178597(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="16bf4-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](/previous-versions/aspnet/ms178597(v=vs.100)).</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="16bf4-108">Mise en cache du service HTTP Web de base</span><span class="sxs-lookup"><span data-stu-id="16bf4-108">Basic Web HTTP Service Caching</span></span>  

  <span data-ttu-id="16bf4-109">Pour activer la mise en cache du service HTTP WEB, vous devez d’abord activer la compatibilité ASP.NET en appliquant au <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> paramètre de service la valeur <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> ou <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required> .</span><span class="sxs-lookup"><span data-stu-id="16bf4-109">To enable WEB HTTP service caching, you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 <span data-ttu-id="16bf4-110">.NET Framework 4 introduit un nouvel attribut appelé <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> qui vous permet de spécifier un nom de profil de cache.</span><span class="sxs-lookup"><span data-stu-id="16bf4-110">.NET Framework 4 introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="16bf4-111">Cet attribut s'applique à une opération de service.</span><span class="sxs-lookup"><span data-stu-id="16bf4-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="16bf4-112">L'exemple suivant applique l'objet <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> à un service pour activer la compatibilité ASP.NET et configure l'opération `GetCustomer` pour la mise en cache.</span><span class="sxs-lookup"><span data-stu-id="16bf4-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="16bf4-113">L'attribut <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> spécifie un profil de cache qui contient les paramètres de cache à utiliser.</span><span class="sxs-lookup"><span data-stu-id="16bf4-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
```csharp
[ServiceContract]
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
<span data-ttu-id="16bf4-114">Activez également le mode de compatibilité ASP.NET dans le fichier Web.config, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="16bf4-114">Also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="16bf4-115">Si le mode de compatibilité ASP.NET n'est pas activé et si l'attribut <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> est utilisé, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="16bf4-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="16bf4-116">Le nom du profil de cache spécifié par l'attribut <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifie un profil de cache qui est ajouté à votre fichier de configuration Web.config.</span><span class="sxs-lookup"><span data-stu-id="16bf4-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="16bf4-117">Le profil de cache est défini avec dans un `outputCacheSetting` élément <> comme indiqué dans l’exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="16bf4-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="16bf4-118">Il s'agit du même élément de configuration que celui disponible pour les applications ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="16bf4-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="16bf4-119">Pour plus d’informations sur les profils de cache ASP.NET, consultez <xref:System.Web.Configuration.OutputCacheProfile> .</span><span class="sxs-lookup"><span data-stu-id="16bf4-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="16bf4-120">Les attributs du profil de cache les plus importants pour les services HTTP Web sont : `cacheDuration` et `varyByParam`.</span><span class="sxs-lookup"><span data-stu-id="16bf4-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="16bf4-121">Ces deux attributs sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="16bf4-121">Both of these attributes are required.</span></span> <span data-ttu-id="16bf4-122">`cacheDuration` définit la durée (en secondes) pendant laquelle une réponse doit être mise en cache.</span><span class="sxs-lookup"><span data-stu-id="16bf4-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="16bf4-123">`varyByParam` vous permet de spécifier un paramètre de chaîne de requête qui est utilisé pour mettre en cache les réponses.</span><span class="sxs-lookup"><span data-stu-id="16bf4-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="16bf4-124">Toutes les demandes effectuées avec des valeurs de paramètre de chaîne de requête différentes sont mises en cache de manière distincte.</span><span class="sxs-lookup"><span data-stu-id="16bf4-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="16bf4-125">Par exemple, une fois qu’une demande initiale est faite à `http://MyServer/MyHttpService/MyOperation?param=10` , toutes les demandes ultérieures effectuées avec le même URI sont retournées à la réponse mise en cache (tant que la durée du cache n’est pas écoulée).</span><span class="sxs-lookup"><span data-stu-id="16bf4-125">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="16bf4-126">Les réponses à une demande similaire, identique mais dont la valeur de paramètre de chaîne de requête est différente, sont mises en cache de manière distincte.</span><span class="sxs-lookup"><span data-stu-id="16bf4-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="16bf4-127">Si vous ne souhaitez pas ce comportement de mise en cache distinct, donnez à l'attribut `varyByParam` la valeur « aucun ».</span><span class="sxs-lookup"><span data-stu-id="16bf4-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="16bf4-128">Dépendance de cache SQL</span><span class="sxs-lookup"><span data-stu-id="16bf4-128">SQL Cache Dependency</span></span>  

  <span data-ttu-id="16bf4-129">Les réponses du service HTTP Web peuvent également être mises en cache avec une dépendance de cache SQL.</span><span class="sxs-lookup"><span data-stu-id="16bf4-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="16bf4-130">Si votre service HTTP Web WCF dépend de données stockées dans une base de données SQL, vous pouvez mettre en cache la réponse du service et invalider la réponse mise en cache lorsque les données dans la table de la base de données SQL changent.</span><span class="sxs-lookup"><span data-stu-id="16bf4-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="16bf4-131">Ce comportement est entièrement configuré dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="16bf4-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="16bf4-132">Tout d’abord, définissez une chaîne de connexion dans l' `connectionStrings` élément <>.</span><span class="sxs-lookup"><span data-stu-id="16bf4-132">First, define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="16bf4-133">Vous devez ensuite activer la dépendance de cache SQL dans un `caching` élément <> au sein de l' `system.web` élément <>, comme indiqué dans l’exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="16bf4-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="16bf4-134">Dans cet exemple, la dépendance de cache SQL est activée et un temps de sondage de 1000 millisecondes est défini.</span><span class="sxs-lookup"><span data-stu-id="16bf4-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="16bf4-135">Chaque fois que le temps de sondage est écoulé, la table de base de données est vérifiée pour détecter les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="16bf4-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="16bf4-136">Si des modifications sont détectées, le contenu du cache est supprimé et lors du prochain appel de l'opération de service, une nouvelle réponse est mise en cache.</span><span class="sxs-lookup"><span data-stu-id="16bf4-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="16bf4-137">Dans l' `sqlCacheDependency` élément <> ajoutez les bases de données et référencez les chaînes de connexion dans l' `databases` élément <> comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="16bf4-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="16bf4-138">Ensuite, vous devez configurer les paramètres du cache de sortie dans l' `caching` élément <> comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="16bf4-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="16bf4-139">Ici, la durée du cache est définie à 60 secondes, `varyByParam` est définie sur aucun et `sqlDependency` est définie sur une liste délimitée par des points-virgules de paires nom/table de base de données séparées par des signes deux-points.</span><span class="sxs-lookup"><span data-stu-id="16bf4-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none, and `sqlDependency` is set to a semicolon-delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="16bf4-140">Lorsque les données dans `MyTable` sont modifiées, la réponse mise en cache pour l'opération de service est supprimée, et lorsque l'opération est appelée, une nouvelle réponse est générée (en appelant l'opération de service), mise en cache et retournée au client.</span><span class="sxs-lookup"><span data-stu-id="16bf4-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="16bf4-141">Pour que ASP.NET accède à une base de données SQL, vous devez utiliser l' [outil d’inscription ASP.NET SQL Server](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="16bf4-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span></span> <span data-ttu-id="16bf4-142">De plus, vous devez autoriser le compte d'utilisateur approprié à accéder à la base de données et à la table.</span><span class="sxs-lookup"><span data-stu-id="16bf4-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="16bf4-143">Pour plus d’informations, consultez [accès à SQL Server à partir d’une application Web](/previous-versions/aspnet/ht43wsex(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="16bf4-143">For more information, see [Accessing SQL Server from a Web Application](/previous-versions/aspnet/ht43wsex(v=vs.100)).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="16bf4-144">Mise en cache basée sur HTTP GET conditionnel</span><span class="sxs-lookup"><span data-stu-id="16bf4-144">Conditional HTTP GET Based Caching</span></span>  

  <span data-ttu-id="16bf4-145">Dans les scénarios HTTP Web, un accès HTTPs conditionnel est souvent utilisé par les services pour implémenter la mise en cache HTTP intelligente, comme décrit dans la [spécification http](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span><span class="sxs-lookup"><span data-stu-id="16bf4-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span></span> <span data-ttu-id="16bf4-146">Pour ce faire, le service doit définir la valeur de l’en-tête ETag dans la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="16bf4-146">To do this, the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="16bf4-147">Il doit également activer l'en-tête If-None-Match dans la requête HTTP pour vérifier si l'un des ETag spécifiés correspond à l'ETag actuel.</span><span class="sxs-lookup"><span data-stu-id="16bf4-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="16bf4-148">Pour les demandes GET et HEAD, la méthode <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> prend une valeur ETag et la compare à l'en-tête If-None-Match de la demande.</span><span class="sxs-lookup"><span data-stu-id="16bf4-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="16bf4-149">Si l’en-tête est présent et qu’il y a une correspondance, un <xref:System.ServiceModel.Web.WebFaultException> avec un code d’état HTTP 304 (non modifié) est levé et un en-tête ETag est ajouté à la réponse avec l’ETag correspondant.</span><span class="sxs-lookup"><span data-stu-id="16bf4-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="16bf4-150">Une surcharge de la méthode <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> prend une date de dernière modification et la compare à l'en-tête If-Modified-Since de la demande.</span><span class="sxs-lookup"><span data-stu-id="16bf4-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="16bf4-151">Si l'en-tête est présent et que la ressource n'a pas été modifiée depuis, une exception <xref:System.ServiceModel.Web.WebFaultException> avec un code d'état HTTP 304 (non modifié) est levée.</span><span class="sxs-lookup"><span data-stu-id="16bf4-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="16bf4-152">Pour les demandes PUT, POST et DELETE, la méthode <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> prend la valeur ETag actuelle d'une ressource.</span><span class="sxs-lookup"><span data-stu-id="16bf4-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="16bf4-153">Si la valeur ETag actuelle est null, la méthode vérifie que l’en-tête If-None-Match a la valeur « \* ».</span><span class="sxs-lookup"><span data-stu-id="16bf4-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="16bf4-154">Si la valeur ETag actuelle n'est pas une valeur par défaut, la méthode vérifie la valeur ETag actuelle par rapport à l'en-tête If- Match de la demande.</span><span class="sxs-lookup"><span data-stu-id="16bf4-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="16bf4-155">Dans l'un et l'autre cas, la méthode lève une exception <xref:System.ServiceModel.Web.WebFaultException> avec un code d'état HTTP 412 (Échec de la condition préalable), si l'en-tête attendu n'est pas présent dans la demande ou si sa valeur ne remplit pas la condition de la vérification, et elle attribue la valeur ETag actuelle à l'en-tête ETag de la réponse.</span><span class="sxs-lookup"><span data-stu-id="16bf4-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="16bf4-156">Les deux méthodes `CheckConditional` et <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> vérifient que la valeur ETag figurant dans l'en-tête de réponse est valide conformément à la spécification HTTP.</span><span class="sxs-lookup"><span data-stu-id="16bf4-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="16bf4-157">Cela implique d'entourer la valeur ETag de guillemets doubles, s'il n'y en a pas déjà, et d'éviter soigneusement les caractères de guillemets doubles internes à la valeur.</span><span class="sxs-lookup"><span data-stu-id="16bf4-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="16bf4-158">La comparaison de valeurs d'ETag faibles n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="16bf4-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="16bf4-159">L'exemple suivant montre l'utilisation de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="16bf4-159">The following example shows how to use these methods.</span></span>  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;

        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a><span data-ttu-id="16bf4-160">Considérations relatives à la sécurité</span><span class="sxs-lookup"><span data-stu-id="16bf4-160">Security Considerations</span></span>  

 <span data-ttu-id="16bf4-161">Les réponses aux demandes qui requièrent une autorisation ne doivent pas être mises en cache, car l'autorisation n'est pas effectuée lorsque la réponse est traitée à partir du cache.</span><span class="sxs-lookup"><span data-stu-id="16bf4-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="16bf4-162">La mise en cache de telles réponses introduirait une faille de sécurité grave.</span><span class="sxs-lookup"><span data-stu-id="16bf4-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="16bf4-163">En règle générale, les demandes qui requièrent une autorisation fournissent des données spécifiques à l'utilisateur, de sorte que la mise en cache côté serveur ne présente aucun avantage.</span><span class="sxs-lookup"><span data-stu-id="16bf4-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="16bf4-164">Dans des situations de ce genre, il est plus approprié d'effectuer une mise en cache côté client, voire aucune mise en cache.</span><span class="sxs-lookup"><span data-stu-id="16bf4-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
