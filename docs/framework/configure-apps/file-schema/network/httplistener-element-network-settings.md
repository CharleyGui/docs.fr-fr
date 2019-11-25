---
title: <httpListener>, élément (paramètres réseau)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 0054be3d2002e4ea5247f25d8094386ac7242422
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088377"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="3bcec-102">\<httpListener >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="3bcec-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="3bcec-103">Personnalise les paramètres utilisés par la classe <xref:System.Net.HttpListener>.</span><span class="sxs-lookup"><span data-stu-id="3bcec-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  

<span data-ttu-id="3bcec-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bcec-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3bcec-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3bcec-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="3bcec-106">&nbsp;&nbsp;&nbsp;&nbsp;[**paramètres**](settings-element-network-settings.md)\<</span><span class="sxs-lookup"><span data-stu-id="3bcec-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\</span></span>
<span data-ttu-id="3bcec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpListener >**</span><span class="sxs-lookup"><span data-stu-id="3bcec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3bcec-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bcec-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="3bcec-109">Tapez</span><span class="sxs-lookup"><span data-stu-id="3bcec-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bcec-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3bcec-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3bcec-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3bcec-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bcec-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="3bcec-112">Attributes</span></span>  
  
|<span data-ttu-id="3bcec-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="3bcec-113">Attribute</span></span>|<span data-ttu-id="3bcec-114">Description</span><span class="sxs-lookup"><span data-stu-id="3bcec-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bcec-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="3bcec-115">unescapeRequestUrl</span></span>|<span data-ttu-id="3bcec-116">Valeur booléenne qui indique si une instance de <xref:System.Net.HttpListener> utilise l’URI brut sans séquence d’échappement au lieu de l’URI converti.</span><span class="sxs-lookup"><span data-stu-id="3bcec-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bcec-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3bcec-117">Child Elements</span></span>  
 <span data-ttu-id="3bcec-118">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="3bcec-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bcec-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3bcec-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3bcec-120">**Élément**</span><span class="sxs-lookup"><span data-stu-id="3bcec-120">**Element**</span></span>|<span data-ttu-id="3bcec-121">**Description**</span><span class="sxs-lookup"><span data-stu-id="3bcec-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3bcec-122">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3bcec-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="3bcec-123">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="3bcec-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bcec-124">Notes</span><span class="sxs-lookup"><span data-stu-id="3bcec-124">Remarks</span></span>  
 <span data-ttu-id="3bcec-125">L’attribut **unescapeRequestUrl** indique si <xref:System.Net.HttpListener> utilise l’URI brut sans séquence d’échappement à la place de l’URI converti dans lequel toutes les valeurs encodées en pourcentage sont converties et d’autres étapes de normalisation sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="3bcec-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="3bcec-126">Lorsqu’une instance de <xref:System.Net.HttpListener> reçoit une demande via le service `http.sys`, elle crée une instance de la chaîne d’URI fournie par `http.sys`et l’expose en tant que propriété <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3bcec-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="3bcec-127">Le service `http.sys` expose deux chaînes d’URI de requête :</span><span class="sxs-lookup"><span data-stu-id="3bcec-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="3bcec-128">URI brut</span><span class="sxs-lookup"><span data-stu-id="3bcec-128">Raw URI</span></span>  
  
- <span data-ttu-id="3bcec-129">URI converti</span><span class="sxs-lookup"><span data-stu-id="3bcec-129">Converted URI</span></span>  
  
 <span data-ttu-id="3bcec-130">L’URI brut est le <xref:System.Uri?displayProperty=nameWithType> fourni dans la ligne de demande d’une requête HTTP :</span><span class="sxs-lookup"><span data-stu-id="3bcec-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="3bcec-131">L’URI brut fourni par `http.sys` pour la demande mentionnée ci-dessus est « /Path/ ».</span><span class="sxs-lookup"><span data-stu-id="3bcec-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="3bcec-132">Cela représente la chaîne qui suit le verbe HTTP tel qu’il a été envoyé sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="3bcec-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="3bcec-133">Le service `http.sys` crée un URI converti à partir des informations fournies dans la demande à l’aide de l’URI fourni dans la ligne de requête HTTP et de l’en-tête de l’hôte pour déterminer le serveur d’origine vers lequel la demande doit être transférée.</span><span class="sxs-lookup"><span data-stu-id="3bcec-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="3bcec-134">Pour ce faire, comparez les informations de la demande avec un ensemble de préfixes URI inscrits.</span><span class="sxs-lookup"><span data-stu-id="3bcec-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="3bcec-135">La documentation du kit de développement logiciel (SDK) du serveur HTTP fait référence à cet URI converti en tant que structure HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="3bcec-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="3bcec-136">Pour pouvoir comparer la demande aux préfixes d’URI inscrits, une certaine normalisation de la demande doit être effectuée.</span><span class="sxs-lookup"><span data-stu-id="3bcec-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="3bcec-137">Pour l’exemple ci-dessus, l’URI converti serait le suivant :</span><span class="sxs-lookup"><span data-stu-id="3bcec-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="3bcec-138">Le service `http.sys` combine la valeur de la propriété <xref:System.Uri.Host%2A?displayProperty=nameWithType> et la chaîne dans la ligne de demande pour créer un URI converti.</span><span class="sxs-lookup"><span data-stu-id="3bcec-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="3bcec-139">En outre, `http.sys` et la classe <xref:System.Uri?displayProperty=nameWithType> effectue également les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3bcec-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="3bcec-140">Annule l’échappement de toutes les valeurs encodées en pourcentage.</span><span class="sxs-lookup"><span data-stu-id="3bcec-140">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="3bcec-141">Convertit des caractères non-ASCII encodés en pourcentage en une représentation de caractères UTF-16.</span><span class="sxs-lookup"><span data-stu-id="3bcec-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="3bcec-142">Notez que les caractères UTF-8 et ANSI/DBCS sont pris en charge, ainsi que les caractères Unicode (encodage Unicode utilisant le format% uXXXX).</span><span class="sxs-lookup"><span data-stu-id="3bcec-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="3bcec-143">Exécute d’autres étapes de normalisation, telles que la compression de chemin.</span><span class="sxs-lookup"><span data-stu-id="3bcec-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="3bcec-144">Étant donné que la demande ne contient pas d’informations sur l’encodage utilisé pour les valeurs encodées en pourcentage, il n’est pas possible de déterminer l’encodage correct en analysant uniquement les valeurs encodées en pourcentage.</span><span class="sxs-lookup"><span data-stu-id="3bcec-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="3bcec-145">Par conséquent `http.sys` fournit deux clés de Registre pour modifier le processus :</span><span class="sxs-lookup"><span data-stu-id="3bcec-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="3bcec-146">Clé de Registre</span><span class="sxs-lookup"><span data-stu-id="3bcec-146">Registry Key</span></span>|<span data-ttu-id="3bcec-147">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="3bcec-147">Default Value</span></span>|<span data-ttu-id="3bcec-148">Description</span><span class="sxs-lookup"><span data-stu-id="3bcec-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="3bcec-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="3bcec-149">EnableNonUTF8</span></span>|<span data-ttu-id="3bcec-150">1</span><span class="sxs-lookup"><span data-stu-id="3bcec-150">1</span></span>|<span data-ttu-id="3bcec-151">Si la valeur est zéro, `http.sys` n’accepte que les URL encodées en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="3bcec-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="3bcec-152">Si la valeur est différente de zéro, `http.sys` accepte également les URL encodées en ANSI ou DBCS dans les demandes.</span><span class="sxs-lookup"><span data-stu-id="3bcec-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="3bcec-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="3bcec-153">FavorUTF8</span></span>|<span data-ttu-id="3bcec-154">1</span><span class="sxs-lookup"><span data-stu-id="3bcec-154">1</span></span>|<span data-ttu-id="3bcec-155">Si la valeur est différente de zéro, `http.sys` essaie toujours de décoder une URL au format UTF-8 en premier ; Si cette conversion échoue et que EnableNonUTF8 est différent de zéro, http. sys essaie ensuite de le décoder en ANSI ou DBCS.</span><span class="sxs-lookup"><span data-stu-id="3bcec-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="3bcec-156">Si zéro (et EnableNonUTF8 est différent de zéro), `http.sys` essaie de le décoder comme ANSI ou DBCS ; Si ce n’est pas le cas, il tente une conversion UTF-8.</span><span class="sxs-lookup"><span data-stu-id="3bcec-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="3bcec-157">Lorsque <xref:System.Net.HttpListener> reçoit une requête, il utilise l’URI converti à partir de `http.sys` comme entrée de la propriété <xref:System.Net.HttpListenerRequest.Url%2A>.</span><span class="sxs-lookup"><span data-stu-id="3bcec-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="3bcec-158">Il est nécessaire de prendre en charge des caractères autres que des caractères et des nombres dans les URI.</span><span class="sxs-lookup"><span data-stu-id="3bcec-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="3bcec-159">Par exemple, l’URI suivant est utilisé pour extraire les informations client pour le numéro de client « 1/3812 » :</span><span class="sxs-lookup"><span data-stu-id="3bcec-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="3bcec-160">Notez la barre oblique encodée en pourcentage dans l’URI (% 2F).</span><span class="sxs-lookup"><span data-stu-id="3bcec-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="3bcec-161">Cela est nécessaire, car dans ce cas, la barre oblique représente des données et non un délimiteur de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="3bcec-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="3bcec-162">Le passage de la chaîne au constructeur d’URI entraîne l’URI suivant :</span><span class="sxs-lookup"><span data-stu-id="3bcec-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="3bcec-163">Le fractionnement du tracé en ses segments entraînerait les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3bcec-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="3bcec-164">Il ne s’agit pas de l’intention de l’expéditeur de la demande.</span><span class="sxs-lookup"><span data-stu-id="3bcec-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="3bcec-165">Si l’attribut **unescapeRequestUrl** est défini sur **false**, lorsque le <xref:System.Net.HttpListener> reçoit une requête, il utilise l’URI brut au lieu de l’URI converti à partir de `http.sys` comme entrée de la propriété <xref:System.Net.HttpListenerRequest.Url%2A>.</span><span class="sxs-lookup"><span data-stu-id="3bcec-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="3bcec-166">La valeur par défaut de l’attribut **unescapeRequestUrl** est **true**.</span><span class="sxs-lookup"><span data-stu-id="3bcec-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="3bcec-167">La propriété <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> peut être utilisée pour récupérer la valeur actuelle de l’attribut **unescapeRequestUrl** à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="3bcec-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bcec-168">Exemple</span><span class="sxs-lookup"><span data-stu-id="3bcec-168">Example</span></span>  
 <span data-ttu-id="3bcec-169">L’exemple suivant montre comment configurer la classe <xref:System.Net.HttpListener> lorsqu’elle reçoit une demande d’utilisation de l’URI brut au lieu de l’URI converti à partir de `http.sys` comme entrée de la propriété <xref:System.Net.HttpListenerRequest.Url%2A>.</span><span class="sxs-lookup"><span data-stu-id="3bcec-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="3bcec-170">Informations sur les éléments</span><span class="sxs-lookup"><span data-stu-id="3bcec-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="3bcec-171">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="3bcec-171">Namespace</span></span>|<span data-ttu-id="3bcec-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="3bcec-172">System.Net</span></span>|  
|<span data-ttu-id="3bcec-173">Nom du schéma</span><span class="sxs-lookup"><span data-stu-id="3bcec-173">Schema Name</span></span>||  
|<span data-ttu-id="3bcec-174">Fichier de validation</span><span class="sxs-lookup"><span data-stu-id="3bcec-174">Validation File</span></span>||  
|<span data-ttu-id="3bcec-175">Peut être vide</span><span class="sxs-lookup"><span data-stu-id="3bcec-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="3bcec-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bcec-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="3bcec-177">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="3bcec-177">Network Settings Schema</span></span>](index.md)
