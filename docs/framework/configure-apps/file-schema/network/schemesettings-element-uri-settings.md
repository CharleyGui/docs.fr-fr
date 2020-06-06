---
title: <schemeSettings>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154645"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="9be8c-102">\<schemeSettings>, élément (paramètres d’URI)</span><span class="sxs-lookup"><span data-stu-id="9be8c-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="9be8c-103">Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.</span><span class="sxs-lookup"><span data-stu-id="9be8c-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="9be8c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9be8c-104">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9be8c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9be8c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9be8c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9be8c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9be8c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="9be8c-107">Attributes</span></span>  
 <span data-ttu-id="9be8c-108">Aucune</span><span class="sxs-lookup"><span data-stu-id="9be8c-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9be8c-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9be8c-109">Child Elements</span></span>  
  
|<span data-ttu-id="9be8c-110">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="9be8c-110">**Element**</span></span>|<span data-ttu-id="9be8c-111">**Description**</span><span class="sxs-lookup"><span data-stu-id="9be8c-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9be8c-112">add</span><span class="sxs-lookup"><span data-stu-id="9be8c-112">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="9be8c-113">Ajoute un paramètre de schéma pour un nom de schéma.</span><span class="sxs-lookup"><span data-stu-id="9be8c-113">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="9be8c-114">clear</span><span class="sxs-lookup"><span data-stu-id="9be8c-114">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="9be8c-115">Efface tous les paramètres de schéma existants.</span><span class="sxs-lookup"><span data-stu-id="9be8c-115">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="9be8c-116">remove</span><span class="sxs-lookup"><span data-stu-id="9be8c-116">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="9be8c-117">Supprime un paramètre de schéma pour un nom de schéma.</span><span class="sxs-lookup"><span data-stu-id="9be8c-117">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9be8c-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9be8c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9be8c-119">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="9be8c-119">**Element**</span></span>|<span data-ttu-id="9be8c-120">**Description**</span><span class="sxs-lookup"><span data-stu-id="9be8c-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9be8c-121">uri</span><span class="sxs-lookup"><span data-stu-id="9be8c-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="9be8c-122">Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="9be8c-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9be8c-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="9be8c-123">Remarks</span></span>  
 <span data-ttu-id="9be8c-124">Par défaut, la <xref:System.Uri?displayProperty=nameWithType> classe annule l’échappement des délimiteurs de chemin d’accès encodés en pourcentage avant d’exécuter la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="9be8c-124">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="9be8c-125">Cela a été implémenté comme un mécanisme de sécurité contre les attaques telles que les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9be8c-125">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="9be8c-126">Si cet URI est passé aux modules qui ne gèrent pas correctement les caractères encodés en pourcentage, cela peut entraîner l’exécution de la commande suivante par le serveur :</span><span class="sxs-lookup"><span data-stu-id="9be8c-126">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="9be8c-127">Pour cette raison, la <xref:System.Uri?displayProperty=nameWithType> classe First annule les délimiteurs de chemin d’accès, puis applique la compression de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="9be8c-127">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="9be8c-128">Le résultat de la transmission de l’URL malveillante ci-dessus au <xref:System.Uri?displayProperty=nameWithType> constructeur de classe génère l’URI suivant :</span><span class="sxs-lookup"><span data-stu-id="9be8c-128">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="9be8c-129">Ce comportement par défaut peut être modifié pour éviter les délimiteurs de chemin d’accès encodés de pourcentage à l’aide de l’option de configuration schemeSettings pour un schéma spécifique.</span><span class="sxs-lookup"><span data-stu-id="9be8c-129">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9be8c-130">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="9be8c-130">Configuration Files</span></span>  
 <span data-ttu-id="9be8c-131">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="9be8c-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9be8c-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="9be8c-132">Example</span></span>  
 <span data-ttu-id="9be8c-133">L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe pour prendre en charge la non-échappement des délimiteurs de chemin d’accès encodés en pourcentage pour le schéma http.</span><span class="sxs-lookup"><span data-stu-id="9be8c-133">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="9be8c-134">Informations sur les éléments</span><span class="sxs-lookup"><span data-stu-id="9be8c-134">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="9be8c-135">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="9be8c-135">Namespace</span></span>|<span data-ttu-id="9be8c-136">Système</span><span class="sxs-lookup"><span data-stu-id="9be8c-136">System</span></span>|  
|<span data-ttu-id="9be8c-137">Nom du schéma</span><span class="sxs-lookup"><span data-stu-id="9be8c-137">Schema Name</span></span>||  
|<span data-ttu-id="9be8c-138">Fichier de validation</span><span class="sxs-lookup"><span data-stu-id="9be8c-138">Validation File</span></span>||  
|<span data-ttu-id="9be8c-139">Peut être vide</span><span class="sxs-lookup"><span data-stu-id="9be8c-139">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="9be8c-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9be8c-140">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="9be8c-141">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="9be8c-141">Network Settings Schema</span></span>](index.md)
