---
title: <clear>, élément de <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: c06fca8b83638fb47bedb21863cb9b200cd211f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927727"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="e91ea-102">\<Clear > élément pour \<configSections ></span><span class="sxs-lookup"><span data-stu-id="e91ea-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="e91ea-103">Efface toutes les sections et tous les groupes de sections précédemment définis.</span><span class="sxs-lookup"><span data-stu-id="e91ea-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="e91ea-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e91ea-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="e91ea-105">&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="e91ea-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="e91ea-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="e91ea-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e91ea-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e91ea-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="e91ea-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="e91ea-108">Attribute</span></span>

|           | <span data-ttu-id="e91ea-109">Description</span><span class="sxs-lookup"><span data-stu-id="e91ea-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="e91ea-110">**name**</span><span class="sxs-lookup"><span data-stu-id="e91ea-110">**name**</span></span>  | <span data-ttu-id="e91ea-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="e91ea-111">Required attribute.</span></span><br><br><span data-ttu-id="e91ea-112">Spécifie le nom de la section ou du groupe de sections à supprimer.</span><span class="sxs-lookup"><span data-stu-id="e91ea-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="e91ea-113">Élément parent</span><span class="sxs-lookup"><span data-stu-id="e91ea-113">Parent element</span></span>

|     | <span data-ttu-id="e91ea-114">Description</span><span class="sxs-lookup"><span data-stu-id="e91ea-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e91ea-115">élément  **>\<configSections**</span><span class="sxs-lookup"><span data-stu-id="e91ea-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="e91ea-116">Contient la section de configuration et les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e91ea-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e91ea-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e91ea-117">Child elements</span></span>

<span data-ttu-id="e91ea-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="e91ea-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="e91ea-119">Notes</span><span class="sxs-lookup"><span data-stu-id="e91ea-119">Remarks</span></span>

<span data-ttu-id="e91ea-120">L’élément clear > supprime tous les sections et groupes de section de votre application qui ont été définis précédemment dans le fichier de configuration actuel ou à un niveau supérieur dans la hiérarchie des fichiers de configuration.  **\<**</span><span class="sxs-lookup"><span data-stu-id="e91ea-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="e91ea-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="e91ea-121">Example</span></span>

<span data-ttu-id="e91ea-122">Cet exemple définit un fichier de configuration d’ordinateur et un fichier de configuration d’application et montre comment utiliser l'  **\<élément clear >** dans un fichier de configuration d’application pour effacer les sections précédemment définies dans la configuration de l’ordinateur. txt.</span><span class="sxs-lookup"><span data-stu-id="e91ea-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="e91ea-123">Le code de fichier de configuration d’ordinateur suivant déclare deux sections,  **\<sampleSection >** et  **\<anotherSampleSection >** , qui sont lues avant le fichier de configuration de l’application:</span><span class="sxs-lookup"><span data-stu-id="e91ea-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

<span data-ttu-id="e91ea-124">Le code de fichier de configuration d’application suivant efface toutes les sections déclarées précédemment.</span><span class="sxs-lookup"><span data-stu-id="e91ea-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="e91ea-125">L’application ne peut pas utiliser ou récupérer les paramètres de l’une des sections qui ont été déclarées dans le fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e91ea-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="e91ea-126">Toutefois, il peut utiliser les paramètres de  **\<anotherSection >** , car il vient après l'  **\<élément clear >** .</span><span class="sxs-lookup"><span data-stu-id="e91ea-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="e91ea-127">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="e91ea-127">Configuration file</span></span>

<span data-ttu-id="e91ea-128">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="e91ea-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="e91ea-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e91ea-129">See also</span></span>

- [<span data-ttu-id="e91ea-130">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e91ea-130">Configuration file schema for the .NET Framework</span></span>](index.md)
