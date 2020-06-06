---
title: Élément personnalisé pour SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: a40f35838655f6021af0b2e966335803ec8c16b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "80635397"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="81859-102">Élément personnalisé pour SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="81859-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="81859-103">Définit des paramètres dans une section de configuration personnalisée qui est définie par un \<section> élément et utilise la <xref:System.Configuration.SingleTagSectionHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="81859-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="81859-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="81859-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="81859-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81859-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="81859-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="81859-106">Attributes</span></span>

<span data-ttu-id="81859-107">Les attributs et les valeurs d’attribut sont définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="81859-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="81859-108">Élément parent</span><span class="sxs-lookup"><span data-stu-id="81859-108">Parent element</span></span>

|     | <span data-ttu-id="81859-109">Description</span><span class="sxs-lookup"><span data-stu-id="81859-109">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="81859-110">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81859-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="81859-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="81859-111">Child elements</span></span>

<span data-ttu-id="81859-112">None</span><span class="sxs-lookup"><span data-stu-id="81859-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="81859-113">Notes</span><span class="sxs-lookup"><span data-stu-id="81859-113">Remarks</span></span>

<span data-ttu-id="81859-114">L' **\<sectionName>** élément est un élément personnalisé défini par une [**\<section>**](section-element.md) balise dans l' [**\<configSections>**](configsections-element-for-configuration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="81859-114">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="81859-115">Le système de configuration retourne un <xref:System.Collections.IDictionary> objet lorsque vous appelez <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="81859-115">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="81859-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="81859-116">Example</span></span>

<span data-ttu-id="81859-117">L’exemple suivant déclare un élément personnalisé appelé **\<sampleSection>** qui contient des paramètres lus par la <xref:System.Configuration.SingleTagSectionHandler> classe :</span><span class="sxs-lookup"><span data-stu-id="81859-117">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="81859-118">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="81859-118">Configuration file</span></span>

<span data-ttu-id="81859-119">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="81859-119">This element can be used in the application configuration file, the machine configuration file (*Machine.config*), and *Web.config* files that aren't at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="81859-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81859-120">See also</span></span>

- [<span data-ttu-id="81859-121">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="81859-121">Configuration file schema for the .NET Framework</span></span>](index.md)
