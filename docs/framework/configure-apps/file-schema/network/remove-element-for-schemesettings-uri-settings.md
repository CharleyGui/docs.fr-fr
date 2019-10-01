---
title: <remove>, élément de schemeSettings (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 0dc8c6111157ba1f23d4a0449bee8f6626027e23
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697860"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="8d2c1-102">Élément @no__t 0remove > pour schemeSettings (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="8d2c1-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="8d2c1-103">Supprime un paramètre de schéma pour un nom de schéma.</span><span class="sxs-lookup"><span data-stu-id="8d2c1-103">Removes a scheme setting for a scheme name.</span></span>  
  
[<span data-ttu-id="8d2c1-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="8d2c1-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="8d2c1-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8d2c1-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="8d2c1-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8d2c1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>  
<span data-ttu-id="8d2c1-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="8d2c1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d2c1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d2c1-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d2c1-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8d2c1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8d2c1-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8d2c1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d2c1-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="8d2c1-111">Attributes</span></span>  
  
|<span data-ttu-id="8d2c1-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="8d2c1-112">Attribute</span></span>|<span data-ttu-id="8d2c1-113">Description</span><span class="sxs-lookup"><span data-stu-id="8d2c1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d2c1-114">name</span><span class="sxs-lookup"><span data-stu-id="8d2c1-114">name</span></span>|<span data-ttu-id="8d2c1-115">Nom du schéma auquel ce paramètre s’applique.</span><span class="sxs-lookup"><span data-stu-id="8d2c1-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="8d2c1-116">Les seules valeurs prises en charge sont Name = "http" et Name = "https".</span><span class="sxs-lookup"><span data-stu-id="8d2c1-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d2c1-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8d2c1-117">Child Elements</span></span>  
 <span data-ttu-id="8d2c1-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8d2c1-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d2c1-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8d2c1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8d2c1-120">Élément</span><span class="sxs-lookup"><span data-stu-id="8d2c1-120">Element</span></span>|<span data-ttu-id="8d2c1-121">Description</span><span class="sxs-lookup"><span data-stu-id="8d2c1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d2c1-122">\<schemeSettings, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="8d2c1-122">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="8d2c1-123">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="8d2c1-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d2c1-124">Notes</span><span class="sxs-lookup"><span data-stu-id="8d2c1-124">Remarks</span></span>  
 <span data-ttu-id="8d2c1-125">Par défaut, la classe <xref:System.Uri?displayProperty=nameWithType> annule l’échappement des délimiteurs de chemin d’accès encodés en pourcentage avant d’exécuter la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="8d2c1-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="8d2c1-126">Cela a été implémenté comme un mécanisme de sécurité contre les attaques telles que les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8d2c1-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="8d2c1-127">Si cet URI est passé aux modules qui ne gèrent pas correctement les caractères encodés en pourcentage, cela peut entraîner l’exécution de la commande suivante par le serveur :</span><span class="sxs-lookup"><span data-stu-id="8d2c1-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="8d2c1-128">C’est la raison pour laquelle la classe <xref:System.Uri?displayProperty=nameWithType> n’ignore pas les délimiteurs de chemin d’accès, puis applique la compression de chemin.</span><span class="sxs-lookup"><span data-stu-id="8d2c1-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="8d2c1-129">Le résultat de la transmission de l’URL malveillante ci-dessus au constructeur de classe <xref:System.Uri?displayProperty=nameWithType> génère l’URI suivant :</span><span class="sxs-lookup"><span data-stu-id="8d2c1-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="8d2c1-130">Ce comportement par défaut peut être modifié pour éviter les délimiteurs de chemin d’accès encodés de pourcentage à l’aide de l’option de configuration schemeSettings pour un schéma spécifique.</span><span class="sxs-lookup"><span data-stu-id="8d2c1-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8d2c1-131">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="8d2c1-131">Configuration Files</span></span>  
 <span data-ttu-id="8d2c1-132">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="8d2c1-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d2c1-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d2c1-133">Example</span></span>  
 <span data-ttu-id="8d2c1-134">L’exemple suivant illustre une configuration utilisée par la classe <xref:System.Uri> qui supprime tous les paramètres de schéma pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="8d2c1-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d2c1-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d2c1-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="8d2c1-136">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="8d2c1-136">Network Settings Schema</span></span>](index.md)
