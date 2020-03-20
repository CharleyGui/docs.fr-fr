---
title: Élément personnalisé pour SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 04360a796b18cf1e414f1f84bff247a1e9d8ef9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155152"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="5e2df-102">Élément personnalisé pour SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="5e2df-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="5e2df-103">Définit les paramètres d’une section de \<configuration personnalisée qui est <xref:System.Configuration.SingleTagSectionHandler> définie par une section> élément et utilise la classe.</span><span class="sxs-lookup"><span data-stu-id="5e2df-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="5e2df-104">&nbsp; &nbsp; [\*\* \<section\*\*](configuration-element.md) *>Name \<>*</span><span class="sxs-lookup"><span data-stu-id="5e2df-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="5e2df-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e2df-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="5e2df-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="5e2df-106">Attributes</span></span>

<span data-ttu-id="5e2df-107">Les attributs et les valeurs d’attribut sont définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5e2df-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="5e2df-108">Élément parent</span><span class="sxs-lookup"><span data-stu-id="5e2df-108">Parent element</span></span>

|     | <span data-ttu-id="5e2df-109">Description</span><span class="sxs-lookup"><span data-stu-id="5e2df-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5e2df-110">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="5e2df-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="5e2df-111">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e2df-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5e2df-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5e2df-112">Child elements</span></span>

<span data-ttu-id="5e2df-113">None</span><span class="sxs-lookup"><span data-stu-id="5e2df-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="5e2df-114">Notes </span><span class="sxs-lookup"><span data-stu-id="5e2df-114">Remarks</span></span>

<span data-ttu-id="5e2df-115">La \*\* \<sectionName>\*\* élément est un élément personnalisé défini par une [\*\* \<section>\*\*](section-element.md) tag dans les [\*\* \<configSections>\*\*](configsections-element-for-configuration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="5e2df-115">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="5e2df-116">Le système de <xref:System.Collections.IDictionary> configuration renvoie un objet lorsque vous appelez <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5e2df-116">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="5e2df-117"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5e2df-117">Example</span></span>

<span data-ttu-id="5e2df-118">L’exemple suivant déclare un élément personnalisé appelé <xref:System.Configuration.SingleTagSectionHandler> \*\* \<sampleSection>\*\* qui contient des paramètres lus par la classe :</span><span class="sxs-lookup"><span data-stu-id="5e2df-118">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="5e2df-119">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="5e2df-119">Configuration file</span></span>

<span data-ttu-id="5e2df-120">Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration de machine (*Machine.config*), et les fichiers *Web.config* qui ne sont pas au niveau de l’annuaire d’application.</span><span class="sxs-lookup"><span data-stu-id="5e2df-120">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e2df-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e2df-121">See also</span></span>

- [<span data-ttu-id="5e2df-122">Schéma de fichier de configuration pour le cadre .NET</span><span class="sxs-lookup"><span data-stu-id="5e2df-122">Configuration file schema for the .NET Framework</span></span>](index.md)
