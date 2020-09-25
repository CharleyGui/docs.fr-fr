---
title: <clear>, élément de schemeSettings (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 17069a56a8647871e98d70826a97a8fe407a0887
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205059"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="5fb9a-102">\<clear>, élément de schemeSettings (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="5fb9a-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="5fb9a-103">Efface tous les paramètres de schéma existants.</span><span class="sxs-lookup"><span data-stu-id="5fb9a-103">Clears all existing scheme settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="5fb9a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fb9a-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fb9a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5fb9a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5fb9a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5fb9a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fb9a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="5fb9a-107">Attributes</span></span>  

 <span data-ttu-id="5fb9a-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5fb9a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5fb9a-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5fb9a-109">Child Elements</span></span>  

 <span data-ttu-id="5fb9a-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5fb9a-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fb9a-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5fb9a-111">Parent Elements</span></span>  
  
|<span data-ttu-id="5fb9a-112">Élément</span><span class="sxs-lookup"><span data-stu-id="5fb9a-112">Element</span></span>|<span data-ttu-id="5fb9a-113">Description</span><span class="sxs-lookup"><span data-stu-id="5fb9a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fb9a-114">\<schemeSettings> , Élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="5fb9a-114">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="5fb9a-115">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="5fb9a-115">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fb9a-116">Notes</span><span class="sxs-lookup"><span data-stu-id="5fb9a-116">Remarks</span></span>  

 <span data-ttu-id="5fb9a-117">Par défaut, la <xref:System.Uri?displayProperty=nameWithType> classe annule l’échappement des délimiteurs de chemin d’accès encodés en pourcentage avant d’exécuter la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="5fb9a-117">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="5fb9a-118">Cela a été implémenté comme un mécanisme de sécurité contre les attaques telles que les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5fb9a-118">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="5fb9a-119">Si cet URI est passé aux modules qui ne gèrent pas correctement les caractères encodés en pourcentage, cela peut entraîner l’exécution de la commande suivante par le serveur :</span><span class="sxs-lookup"><span data-stu-id="5fb9a-119">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="5fb9a-120">Pour cette raison, la <xref:System.Uri?displayProperty=nameWithType> classe First annule les délimiteurs de chemin d’accès, puis applique la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="5fb9a-120">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="5fb9a-121">Le résultat de la transmission de l’URL malveillante ci-dessus au <xref:System.Uri?displayProperty=nameWithType> constructeur de classe génère l’URI suivant :</span><span class="sxs-lookup"><span data-stu-id="5fb9a-121">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="5fb9a-122">Ce comportement par défaut peut être modifié pour éviter les délimiteurs de chemin d’accès encodés de pourcentage à l’aide de l’option de configuration schemeSettings pour un schéma spécifique.</span><span class="sxs-lookup"><span data-stu-id="5fb9a-122">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5fb9a-123">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5fb9a-123">Configuration Files</span></span>  

 <span data-ttu-id="5fb9a-124">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5fb9a-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fb9a-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="5fb9a-125">Example</span></span>  

 <span data-ttu-id="5fb9a-126">L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe qui efface tous les paramètres de schéma, puis ajoute la prise en charge pour ne pas échapper les délimiteurs de chemin d’accès encodés en pourcentage pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="5fb9a-126">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fb9a-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fb9a-127">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="5fb9a-128">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="5fb9a-128">Network Settings Schema</span></span>](index.md)
