---
title: <schemeSettings>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154645"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="e581b-102">\<schemeSettings, élément (paramètres d’Uri)</span><span class="sxs-lookup"><span data-stu-id="e581b-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="e581b-103">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e581b-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[<span data-ttu-id="e581b-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="e581b-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e581b-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e581b-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="e581b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<schémasSettings>**</span><span class="sxs-lookup"><span data-stu-id="e581b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e581b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e581b-107">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e581b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e581b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e581b-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e581b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e581b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="e581b-110">Attributes</span></span>  
 <span data-ttu-id="e581b-111">None</span><span class="sxs-lookup"><span data-stu-id="e581b-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e581b-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e581b-112">Child Elements</span></span>  
  
|<span data-ttu-id="e581b-113">**Élément**</span><span class="sxs-lookup"><span data-stu-id="e581b-113">**Element**</span></span>|<span data-ttu-id="e581b-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="e581b-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e581b-115">ajouter</span><span class="sxs-lookup"><span data-stu-id="e581b-115">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="e581b-116">Ajoute un paramètre de régime pour un nom de régime.</span><span class="sxs-lookup"><span data-stu-id="e581b-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="e581b-117">Clair</span><span class="sxs-lookup"><span data-stu-id="e581b-117">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="e581b-118">Efface tous les paramètres de schéma existants.</span><span class="sxs-lookup"><span data-stu-id="e581b-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="e581b-119">retirer</span><span class="sxs-lookup"><span data-stu-id="e581b-119">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="e581b-120">Supprime un paramètre de régime pour un nom de régime.</span><span class="sxs-lookup"><span data-stu-id="e581b-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e581b-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e581b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e581b-122">**Élément**</span><span class="sxs-lookup"><span data-stu-id="e581b-122">**Element**</span></span>|<span data-ttu-id="e581b-123">**Description**</span><span class="sxs-lookup"><span data-stu-id="e581b-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e581b-124">Uri</span><span class="sxs-lookup"><span data-stu-id="e581b-124">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="e581b-125">Contient des paramètres qui spécifient comment le cadre .NET gère les adresses Web exprimées à l’aide d’identifiants de ressources uniformes (IER).</span><span class="sxs-lookup"><span data-stu-id="e581b-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e581b-126">Notes </span><span class="sxs-lookup"><span data-stu-id="e581b-126">Remarks</span></span>  
 <span data-ttu-id="e581b-127">Par défaut, <xref:System.Uri?displayProperty=nameWithType> la classe n’échappe pas pour cent encodé les délimitations de chemin avant d’exécuter la compression de chemin.</span><span class="sxs-lookup"><span data-stu-id="e581b-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="e581b-128">Ceci a été mis en œuvre comme un mécanisme de sécurité contre des attaques comme les suivantes:</span><span class="sxs-lookup"><span data-stu-id="e581b-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="e581b-129">Si cette URI est transmise à des modules ne manipulant pas les pourcentage de caractères codés correctement, cela pourrait entraîner l’exécution de la commande suivante par le serveur :</span><span class="sxs-lookup"><span data-stu-id="e581b-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="e581b-130">Pour cette <xref:System.Uri?displayProperty=nameWithType> raison, la classe d’abord délimiters chemin d’évacuation et applique ensuite la compression de chemin.</span><span class="sxs-lookup"><span data-stu-id="e581b-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="e581b-131">Le résultat de la transmission <xref:System.Uri?displayProperty=nameWithType> de l’URL malveillante ci-dessus au constructeur de classe se traduit par l’URI suivante:</span><span class="sxs-lookup"><span data-stu-id="e581b-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="e581b-132">Ce comportement par défaut peut être modifié pour ne pas délimiters chemin décodé pour un moyen d’évasion encodé en utilisant l’option de configuration schemeSettings pour un schéma spécifique.</span><span class="sxs-lookup"><span data-stu-id="e581b-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e581b-133">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="e581b-133">Configuration Files</span></span>  
 <span data-ttu-id="e581b-134">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e581b-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e581b-135"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e581b-135">Example</span></span>  
 <span data-ttu-id="e581b-136">L’exemple suivant montre une <xref:System.Uri> configuration utilisée par la classe pour soutenir ne pas échapper à des délimitations de chemin encodé pour le système http.</span><span class="sxs-lookup"><span data-stu-id="e581b-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="e581b-137">Informations sur les éléments</span><span class="sxs-lookup"><span data-stu-id="e581b-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="e581b-138">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="e581b-138">Namespace</span></span>|<span data-ttu-id="e581b-139">Système</span><span class="sxs-lookup"><span data-stu-id="e581b-139">System</span></span>|  
|<span data-ttu-id="e581b-140">Nom du schéma</span><span class="sxs-lookup"><span data-stu-id="e581b-140">Schema Name</span></span>||  
|<span data-ttu-id="e581b-141">Fichier de validation</span><span class="sxs-lookup"><span data-stu-id="e581b-141">Validation File</span></span>||  
|<span data-ttu-id="e581b-142">Peut être vide</span><span class="sxs-lookup"><span data-stu-id="e581b-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="e581b-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e581b-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="e581b-144">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="e581b-144">Network Settings Schema</span></span>](index.md)
