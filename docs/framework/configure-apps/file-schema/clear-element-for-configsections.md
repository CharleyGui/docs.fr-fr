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
ms.openlocfilehash: e79def513637937262d00b0edb1b0f7676fd120b
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300801"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="f2c91-102">\<Désactivez >, élément pour \<configSections ></span><span class="sxs-lookup"><span data-stu-id="f2c91-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="f2c91-103">Efface toutes les sections précédemment définies et les groupes de sections.</span><span class="sxs-lookup"><span data-stu-id="f2c91-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="f2c91-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f2c91-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="f2c91-105">&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f2c91-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="f2c91-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="f2c91-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f2c91-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2c91-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="f2c91-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f2c91-108">Attribute</span></span>

|           | <span data-ttu-id="f2c91-109">Description</span><span class="sxs-lookup"><span data-stu-id="f2c91-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f2c91-110">**name**</span><span class="sxs-lookup"><span data-stu-id="f2c91-110">**name**</span></span>  | <span data-ttu-id="f2c91-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="f2c91-111">Required attribute.</span></span><br><br><span data-ttu-id="f2c91-112">Spécifie le nom de la section ou le groupe de section à supprimer.</span><span class="sxs-lookup"><span data-stu-id="f2c91-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f2c91-113">Élément parent</span><span class="sxs-lookup"><span data-stu-id="f2c91-113">Parent element</span></span>

|     | <span data-ttu-id="f2c91-114">Description</span><span class="sxs-lookup"><span data-stu-id="f2c91-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f2c91-115"> *\*\<configSections >** élément</span><span class="sxs-lookup"><span data-stu-id="f2c91-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="f2c91-116">Contient des déclarations d’espace de noms et de la section de configuration.</span><span class="sxs-lookup"><span data-stu-id="f2c91-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f2c91-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f2c91-117">Child elements</span></span>

<span data-ttu-id="f2c91-118">None</span><span class="sxs-lookup"><span data-stu-id="f2c91-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="f2c91-119">Notes</span><span class="sxs-lookup"><span data-stu-id="f2c91-119">Remarks</span></span>

<span data-ttu-id="f2c91-120">Le  **\<Effacer >** élément supprime toutes les sections et groupes de votre application qui ont été définis précédemment dans le fichier de configuration actuel ou à un niveau supérieur dans la hiérarchie de fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="f2c91-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="f2c91-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="f2c91-121">Example</span></span>

<span data-ttu-id="f2c91-122">Cet exemple définit un fichier de configuration d’ordinateur et un fichier de configuration d’application et montre comment utiliser le  **\<Effacer >** élément dans un fichier de configuration d’application pour effacer les sections définies précédemment dans le fichier de configuration machine.</span><span class="sxs-lookup"><span data-stu-id="f2c91-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="f2c91-123">Le code du fichier de configuration machine suivant déclare deux sections,  **\<sampleSection >** et  **\<anotherSampleSection >** , qui sont lus avant que l’application fichier de configuration :</span><span class="sxs-lookup"><span data-stu-id="f2c91-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

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

<span data-ttu-id="f2c91-124">Le code suivant du fichier de configuration de l’application efface toutes les sections déclarées précédemment.</span><span class="sxs-lookup"><span data-stu-id="f2c91-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="f2c91-125">L’application ne peut pas utiliser ou récupérer des paramètres dans les sections qui ont été déclarées dans le fichier de configuration machine.</span><span class="sxs-lookup"><span data-stu-id="f2c91-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="f2c91-126">Toutefois, il peut utiliser les paramètres à partir de  **\<anotherSection >** , car elle vient après le  **\<Effacer >** élément.</span><span class="sxs-lookup"><span data-stu-id="f2c91-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="f2c91-127">fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="f2c91-127">Configuration file</span></span>

<span data-ttu-id="f2c91-128">Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration machine (*Machine.config*), et *Web.config* fichiers qui ne sont pas au niveau du répertoire d’application.</span><span class="sxs-lookup"><span data-stu-id="f2c91-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2c91-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2c91-129">See also</span></span>

- [<span data-ttu-id="f2c91-130">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f2c91-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
