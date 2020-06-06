---
title: Élément personnalisé pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215479"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="07edf-102">Élément personnalisé pour NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="07edf-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="07edf-103">Définit des paramètres pour les sections de configuration personnalisées qui utilisent les <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> classes et.</span><span class="sxs-lookup"><span data-stu-id="07edf-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a><span data-ttu-id="07edf-104">Attributs</span><span class="sxs-lookup"><span data-stu-id="07edf-104">Attributes</span></span>

<span data-ttu-id="07edf-105">Aucune</span><span class="sxs-lookup"><span data-stu-id="07edf-105">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="07edf-106">Élément parent</span><span class="sxs-lookup"><span data-stu-id="07edf-106">Parent element</span></span>

|     | <span data-ttu-id="07edf-107">Description</span><span class="sxs-lookup"><span data-stu-id="07edf-107">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="07edf-108">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07edf-108">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="07edf-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="07edf-109">Child elements</span></span>

|     | <span data-ttu-id="07edf-110">Description</span><span class="sxs-lookup"><span data-stu-id="07edf-110">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="07edf-111">[**\<add>**](add-element-for-custom-2.md)pour <xref:System.Configuration.NameValueSectionHandler> et<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="07edf-111">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="07edf-112">Ajoute des paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="07edf-112">Adds custom application settings.</span></span> |
| <span data-ttu-id="07edf-113">[**\<remove>**](remove-element-for-custom-2.md)pour <xref:System.Configuration.NameValueSectionHandler> et<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="07edf-113">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="07edf-114">Supprime un paramètre défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="07edf-114">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="07edf-115">[**\<clear>**](clear-element-for-custom-2.md)pour <xref:System.Configuration.NameValueSectionHandler> et<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="07edf-115">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="07edf-116">Efface tous les paramètres précédemment définis dans une section.</span><span class="sxs-lookup"><span data-stu-id="07edf-116">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="07edf-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="07edf-117">Remarks</span></span>

<span data-ttu-id="07edf-118">L' **\<sectionName>** élément est un élément personnalisé défini par une **\<section>** balise dans l' **\<configSections>** élément.</span><span class="sxs-lookup"><span data-stu-id="07edf-118">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="07edf-119">Le tableau suivant indique le type d’objet retourné par la méthode ConfigurationSettings. GetConfig pour chaque gestionnaire de section de configuration :</span><span class="sxs-lookup"><span data-stu-id="07edf-119">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="07edf-120">Gestionnaire de section de configuration</span><span class="sxs-lookup"><span data-stu-id="07edf-120">Configuration section handler</span></span>                        | <span data-ttu-id="07edf-121">Type de retour</span><span class="sxs-lookup"><span data-stu-id="07edf-121">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="07edf-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="07edf-122">Example</span></span>

<span data-ttu-id="07edf-123">L’exemple suivant montre comment déclarer des sections qui utilisent les <xref:System.Configuration.DictionarySectionHandler> <xref:System.Configuration.NameValueSectionHandler> classes et.</span><span class="sxs-lookup"><span data-stu-id="07edf-123">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="07edf-124">Le premier élément personnalisé est **\<dictionarySample>** , qui contient les paramètres lus par la <xref:System.Configuration.DictionarySectionHandler> classe dans l' `System.dll` assembly.</span><span class="sxs-lookup"><span data-stu-id="07edf-124">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="07edf-125">Le deuxième élément personnalisé est **\<mySection>** , qui contient les paramètres lus par la <xref:System.Configuration.NameValueSectionHandler> classe dans l' `System.dll` assembly.</span><span class="sxs-lookup"><span data-stu-id="07edf-125">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="07edf-126">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="07edf-126">Configuration file</span></span>

<span data-ttu-id="07edf-127">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="07edf-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="07edf-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07edf-128">See also</span></span>

- [<span data-ttu-id="07edf-129">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="07edf-129">Configuration file schema for the .NET Framework</span></span>](index.md)
