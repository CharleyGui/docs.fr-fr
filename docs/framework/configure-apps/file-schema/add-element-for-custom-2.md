---
title: <add>, élément de NameValueSectionHandler et DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215434"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="4f8d8-102">\<add>, élément de NameValueSectionHandler et DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="4f8d8-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="4f8d8-103">Ajoute des paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="4f8d8-103">Adds custom application settings.</span></span> <span data-ttu-id="4f8d8-104">Chaque **\<add>** balise contient une paire clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="4f8d8-104">Each **\<add>** tag contains a key/value pair.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="4f8d8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f8d8-105">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="4f8d8-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="4f8d8-106">Attributes</span></span>

| <span data-ttu-id="4f8d8-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="4f8d8-107">Attribute</span></span> | <span data-ttu-id="4f8d8-108">Description</span><span class="sxs-lookup"><span data-stu-id="4f8d8-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4f8d8-109">**key**</span><span class="sxs-lookup"><span data-stu-id="4f8d8-109">**key**</span></span>   | <span data-ttu-id="4f8d8-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="4f8d8-110">Required attribute.</span></span><br><br><span data-ttu-id="4f8d8-111">Spécifie le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="4f8d8-111">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="4f8d8-112">**value**</span><span class="sxs-lookup"><span data-stu-id="4f8d8-112">**value**</span></span> | <span data-ttu-id="4f8d8-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="4f8d8-113">Required attribute.</span></span><br><br><span data-ttu-id="4f8d8-114">Spécifie la valeur du paramètre.</span><span class="sxs-lookup"><span data-stu-id="4f8d8-114">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="4f8d8-115">Élément parent</span><span class="sxs-lookup"><span data-stu-id="4f8d8-115">Parent element</span></span>

| <span data-ttu-id="4f8d8-116">Élément</span><span class="sxs-lookup"><span data-stu-id="4f8d8-116">Element</span></span> | <span data-ttu-id="4f8d8-117">Description</span><span class="sxs-lookup"><span data-stu-id="4f8d8-117">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="4f8d8-118">**\<sectionName>** Appartient</span><span class="sxs-lookup"><span data-stu-id="4f8d8-118">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="4f8d8-119">Définit des paramètres pour les sections de configuration personnalisées qui utilisent les <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> classes et.</span><span class="sxs-lookup"><span data-stu-id="4f8d8-119">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4f8d8-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4f8d8-120">Child elements</span></span>

<span data-ttu-id="4f8d8-121">None</span><span class="sxs-lookup"><span data-stu-id="4f8d8-121">None</span></span>

## <a name="example"></a><span data-ttu-id="4f8d8-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="4f8d8-122">Example</span></span>

<span data-ttu-id="4f8d8-123">L’exemple suivant montre comment définir une section de configuration personnalisée et comment utiliser l' **\<add>** élément pour placer des paramètres dans la section :</span><span class="sxs-lookup"><span data-stu-id="4f8d8-123">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="4f8d8-124">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="4f8d8-124">Configuration file</span></span>

<span data-ttu-id="4f8d8-125">Cet élément peut être utilisé dans le fichier de configuration de l’application, le fichier de configuration de l’ordinateur (*machine. config*) et les fichiers *Web. config* qui ne sont pas au niveau du répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="4f8d8-125">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f8d8-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f8d8-126">See also</span></span>

- [<span data-ttu-id="4f8d8-127">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4f8d8-127">Configuration file schema for the .NET Framework</span></span>](index.md)
