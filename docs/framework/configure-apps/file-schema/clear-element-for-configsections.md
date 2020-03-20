---
title: <clear>, élément de <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155425"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="e461b-102">\<un élément clair> \<pour les> de configSections</span><span class="sxs-lookup"><span data-stu-id="e461b-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="e461b-103">Efface toutes les sections et les groupes de section précédemment définis.</span><span class="sxs-lookup"><span data-stu-id="e461b-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="e461b-104">&nbsp; &nbsp; &nbsp; &nbsp; \*\* \<\*\* [**les \<**](configuration-element.md) [**>les configections>claires>\<**](configsections-element-for-configuration.md) &nbsp; &nbsp;</span><span class="sxs-lookup"><span data-stu-id="e461b-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e461b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e461b-105">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="e461b-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="e461b-106">Attribute</span></span>

|           | <span data-ttu-id="e461b-107">Description</span><span class="sxs-lookup"><span data-stu-id="e461b-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="e461b-108">**name**</span><span class="sxs-lookup"><span data-stu-id="e461b-108">**name**</span></span>  | <span data-ttu-id="e461b-109">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="e461b-109">Required attribute.</span></span><br><br><span data-ttu-id="e461b-110">Spécifie le nom de la section ou du groupe de section à supprimer.</span><span class="sxs-lookup"><span data-stu-id="e461b-110">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="e461b-111">Élément parent</span><span class="sxs-lookup"><span data-stu-id="e461b-111">Parent element</span></span>

|     | <span data-ttu-id="e461b-112">Description</span><span class="sxs-lookup"><span data-stu-id="e461b-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e461b-113">les>des configections \*\* \<\*\* Élément</span><span class="sxs-lookup"><span data-stu-id="e461b-113">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="e461b-114">Contient la section de configuration et les déclarations d’espace nom.</span><span class="sxs-lookup"><span data-stu-id="e461b-114">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e461b-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e461b-115">Child elements</span></span>

<span data-ttu-id="e461b-116">None</span><span class="sxs-lookup"><span data-stu-id="e461b-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="e461b-117">Notes </span><span class="sxs-lookup"><span data-stu-id="e461b-117">Remarks</span></span>

<span data-ttu-id="e461b-118">\*\* \<L’élément>clair\*\* supprime toutes les sections et les groupes de section de votre application qui ont été définis plus tôt dans le fichier de configuration actuel ou à un niveau supérieur dans la hiérarchie des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="e461b-118">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="e461b-119"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e461b-119">Example</span></span>

<span data-ttu-id="e461b-120">Cet exemple définit un fichier de configuration de machine et un fichier de configuration d’application et montre comment utiliser \*\* \<l’élément>clair\*\* dans un fichier de configuration d’application pour effacer les sections précédemment définies dans le fichier de configuration de la machine.</span><span class="sxs-lookup"><span data-stu-id="e461b-120">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="e461b-121">Le code de fichier de configuration de la machine suivante \*\* \< **déclare deux sections, \*\* \<l’échantillonSection>** et un autre>de la configuration de la machine, qui sont lus avant le fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="e461b-121">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

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

<span data-ttu-id="e461b-122">Le code de fichier de configuration d’application suivant efface toutes les sections précédemment déclarées.</span><span class="sxs-lookup"><span data-stu-id="e461b-122">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="e461b-123">L’application ne peut pas utiliser ou récupérer les paramètres dans l’une ou l’autre des sections qui ont été déclarées dans le fichier de configuration de la machine.</span><span class="sxs-lookup"><span data-stu-id="e461b-123">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="e461b-124">Cependant, il peut utiliser les paramètres \*\* \<d’un autre>\*\* de la section parce qu’il vient après \*\* \<l’élément clair>.\*\*</span><span class="sxs-lookup"><span data-stu-id="e461b-124">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="e461b-125">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="e461b-125">Configuration file</span></span>

<span data-ttu-id="e461b-126">Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration de machine (*Machine.config*), et les fichiers *Web.config* qui ne sont pas au niveau de l’annuaire d’application.</span><span class="sxs-lookup"><span data-stu-id="e461b-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="e461b-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e461b-127">See also</span></span>

- [<span data-ttu-id="e461b-128">Schéma de fichier de configuration pour le cadre .NET</span><span class="sxs-lookup"><span data-stu-id="e461b-128">Configuration file schema for the .NET Framework</span></span>](index.md)
