---
title: Élément personnalisé pour NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215479"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="189b0-102">Élément personnalisé pour NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="189b0-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="189b0-103">Définit les paramètres des sections de configuration personnalisées qui utilisent les classes <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="189b0-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="189b0-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="189b0-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="189b0-105">&nbsp;&nbsp; **\<** de la ></span><span class="sxs-lookup"><span data-stu-id="189b0-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="189b0-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="189b0-106">Attributes</span></span>

<span data-ttu-id="189b0-107">None</span><span class="sxs-lookup"><span data-stu-id="189b0-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="189b0-108">Élément parent</span><span class="sxs-lookup"><span data-stu-id="189b0-108">Parent element</span></span>

|     | <span data-ttu-id="189b0-109">Description</span><span class="sxs-lookup"><span data-stu-id="189b0-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="189b0-110"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="189b0-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="189b0-111">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="189b0-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="189b0-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="189b0-112">Child elements</span></span>

|     | <span data-ttu-id="189b0-113">Description</span><span class="sxs-lookup"><span data-stu-id="189b0-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="189b0-114">[ **\<ajouter des >** ](add-element-for-custom-2.md) pour <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="189b0-114">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="189b0-115">Ajoute des paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="189b0-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="189b0-116">[ **\<supprimer >** ](remove-element-for-custom-2.md) pour <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="189b0-116">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="189b0-117">Supprime un paramètre défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="189b0-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="189b0-118">[ **\<> Clear**](clear-element-for-custom-2.md) pour <xref:System.Configuration.NameValueSectionHandler> et <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="189b0-118">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="189b0-119">Efface tous les paramètres précédemment définis dans une section.</span><span class="sxs-lookup"><span data-stu-id="189b0-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="189b0-120">Notes</span><span class="sxs-lookup"><span data-stu-id="189b0-120">Remarks</span></span>

<span data-ttu-id="189b0-121">L’élément\<de l’élément de **>** est un élément personnalisé défini par un **\<section >** balise dans l’élément **\<configSections >** .</span><span class="sxs-lookup"><span data-stu-id="189b0-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="189b0-122">Le tableau suivant indique le type d’objet retourné par la méthode ConfigurationSettings. GetConfig pour chaque gestionnaire de section de configuration :</span><span class="sxs-lookup"><span data-stu-id="189b0-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="189b0-123">Gestionnaire de section de configuration</span><span class="sxs-lookup"><span data-stu-id="189b0-123">Configuration section handler</span></span>                        | <span data-ttu-id="189b0-124">Type de retour</span><span class="sxs-lookup"><span data-stu-id="189b0-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="189b0-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="189b0-125">Example</span></span>

<span data-ttu-id="189b0-126">L’exemple suivant montre comment déclarer des sections qui utilisent les classes <xref:System.Configuration.DictionarySectionHandler> et <xref:System.Configuration.NameValueSectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="189b0-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="189b0-127">Le premier élément personnalisé est **\<dictionarySample >** , qui contient les paramètres lus par la classe <xref:System.Configuration.DictionarySectionHandler> de l’assembly `System.dll`.</span><span class="sxs-lookup"><span data-stu-id="189b0-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="189b0-128">Le deuxième élément personnalisé est **\<mySection >** , qui contient les paramètres lus par la classe <xref:System.Configuration.NameValueSectionHandler> de l’assembly `System.dll`.</span><span class="sxs-lookup"><span data-stu-id="189b0-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="189b0-129">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="189b0-129">Configuration file</span></span>

<span data-ttu-id="189b0-130">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="189b0-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="189b0-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="189b0-131">See also</span></span>

- [<span data-ttu-id="189b0-132">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="189b0-132">Configuration file schema for the .NET Framework</span></span>](index.md)
