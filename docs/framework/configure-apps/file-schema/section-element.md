---
title: <section> element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153726"
---
# <a name="section-element"></a><span data-ttu-id="27353-102">\<section> élément</span><span class="sxs-lookup"><span data-stu-id="27353-102">\<section> element</span></span>

<span data-ttu-id="27353-103">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="27353-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="27353-104">[**\<configuration>**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="27353-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="27353-105">&nbsp;&nbsp;[**\<les>**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="27353-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="27353-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span><span class="sxs-lookup"><span data-stu-id="27353-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="27353-107">[**\<configuration>**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="27353-107">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="27353-108">&nbsp;&nbsp;[**\<les>**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="27353-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="27353-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroupe>**](sectiongroup-element-for-configsections.md)</span><span class="sxs-lookup"><span data-stu-id="27353-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)</span></span>\
<span data-ttu-id="27353-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span><span class="sxs-lookup"><span data-stu-id="27353-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="27353-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27353-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="27353-112">Attributs requis</span><span class="sxs-lookup"><span data-stu-id="27353-112">Required attributes</span></span>

|           | <span data-ttu-id="27353-113">Description</span><span class="sxs-lookup"><span data-stu-id="27353-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="27353-114">**name**</span><span class="sxs-lookup"><span data-stu-id="27353-114">**name**</span></span>  | <span data-ttu-id="27353-115">Spécifie le nom de la section configuration.</span><span class="sxs-lookup"><span data-stu-id="27353-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="27353-116">**type**</span><span class="sxs-lookup"><span data-stu-id="27353-116">**type**</span></span>  | <span data-ttu-id="27353-117">Spécifie le nom de la classe de gestionnaire de section de configuration qui lit la section à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="27353-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="27353-118">La valeur type a la syntaxe "entièrement qualifié-section-gestionnaire-classe nom, simple-assemblage-nom".</span><span class="sxs-lookup"><span data-stu-id="27353-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="27353-119">Le nom d’assemblage simple est le nom de fichier racine sans l’extension de fichier *.dll.*</span><span class="sxs-lookup"><span data-stu-id="27353-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="27353-120">Attributs facultatifs</span><span class="sxs-lookup"><span data-stu-id="27353-120">Optional attributes</span></span>

<span data-ttu-id="27353-121">Les attributs suivants ne s’appliquent qu’aux applications ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="27353-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="27353-122">Le système de configuration ignore ces attributs pour d’autres types d’applications.</span><span class="sxs-lookup"><span data-stu-id="27353-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="27353-123">Description</span><span class="sxs-lookup"><span data-stu-id="27353-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="27353-124">**permettreDefinition**</span><span class="sxs-lookup"><span data-stu-id="27353-124">**allowDefinition**</span></span> | <span data-ttu-id="27353-125">Précise dans quel fichier de configuration la section peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="27353-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="27353-126">Utilisez l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="27353-126">Use one of the following values:</span></span><br><br><span data-ttu-id="27353-127">**Partout**</span><span class="sxs-lookup"><span data-stu-id="27353-127">**Everywhere**</span></span><br><span data-ttu-id="27353-128">Permet d’utiliser la section dans n’importe quel fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="27353-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="27353-129">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="27353-129">This is the default.</span></span><br><span data-ttu-id="27353-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="27353-130">**MachineOnly**</span></span><br><span data-ttu-id="27353-131">Permet à la section d’être utilisée uniquement dans le fichier de configuration de la machine (*Machine.config*).</span><span class="sxs-lookup"><span data-stu-id="27353-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="27353-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="27353-132">**MachineToApplication**</span></span><br><span data-ttu-id="27353-133">Permet d’utiliser la section dans le fichier de configuration de la machine ou dans le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="27353-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="27353-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="27353-134">**allowLocation**</span></span>   | <span data-ttu-id="27353-135">Détermine si la section peut être utilisée dans \*\* \<l’emplacement>\*\* élément.</span><span class="sxs-lookup"><span data-stu-id="27353-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="27353-136">Utilisez l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="27353-136">Use one of the following values:</span></span><br><br><span data-ttu-id="27353-137">**true**</span><span class="sxs-lookup"><span data-stu-id="27353-137">**true**</span></span><br><span data-ttu-id="27353-138">Permet d’utiliser la section dans \*\* \<l’emplacement>\*\* élément.</span><span class="sxs-lookup"><span data-stu-id="27353-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="27353-139">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="27353-139">This is the default.</span></span><br><span data-ttu-id="27353-140">**false**</span><span class="sxs-lookup"><span data-stu-id="27353-140">**false**</span></span><br><span data-ttu-id="27353-141">Ne permet pas que la section soit utilisée dans \*\* \<l’emplacement>\*\* élément.</span><span class="sxs-lookup"><span data-stu-id="27353-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="27353-142">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="27353-142">Parent elements</span></span>

|     | <span data-ttu-id="27353-143">Description</span><span class="sxs-lookup"><span data-stu-id="27353-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="27353-144">les>des configections \*\* \<\*\* Élément</span><span class="sxs-lookup"><span data-stu-id="27353-144">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="27353-145">Contient la section de configuration et les déclarations d’espace nom.</span><span class="sxs-lookup"><span data-stu-id="27353-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="27353-146">\*\* \<sectionGroupe>\*\* Élément</span><span class="sxs-lookup"><span data-stu-id="27353-146">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="27353-147">Définit un espace de nom pour les sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="27353-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="27353-148">Une \*\* \<section>\*\* élément est un élément enfant des \*\* \<configSections>\*\* ou \*\* \<de la sectionGroup>\*\* mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="27353-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="27353-149">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="27353-149">Child elements</span></span>

<span data-ttu-id="27353-150">None</span><span class="sxs-lookup"><span data-stu-id="27353-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="27353-151">Notes </span><span class="sxs-lookup"><span data-stu-id="27353-151">Remarks</span></span>

<span data-ttu-id="27353-152">La déclaration d’une section de configuration définit essentiellement un nouvel élément pour le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="27353-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="27353-153">Le nouvel élément contient des paramètres qu’un gestionnaire de <xref:System.Configuration.IConfigurationSectionHandler> section de configuration (c’est-à-dire une classe qui implémente l’interface) lit.</span><span class="sxs-lookup"><span data-stu-id="27353-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="27353-154">Les attributs et les éléments pour enfants d’une section que vous définissez dépendent du gestionnaire de section que vous utilisez pour lire vos paramètres.</span><span class="sxs-lookup"><span data-stu-id="27353-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="27353-155">Déclarer un gestionnaire de section de configuration dans le fichier *Machine.config* vous permet d’utiliser la section de configuration dans n’importe quel fichier de configuration d’application sur cet ordinateur, à moins que l’attribut **de définition de permis** ne spécifie le contraire.</span><span class="sxs-lookup"><span data-stu-id="27353-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="27353-156"> Exemple</span><span class="sxs-lookup"><span data-stu-id="27353-156">Example</span></span>

<span data-ttu-id="27353-157">L’exemple suivant montre comment définir une section de configuration et définir les paramètres de cette section :</span><span class="sxs-lookup"><span data-stu-id="27353-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler"
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="27353-158">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="27353-158">Configuration file</span></span>

<span data-ttu-id="27353-159">Cet élément peut être utilisé dans le fichier de configuration d’application, fichier de configuration de machine (*Machine.config*), et les fichiers *Web.config* qui ne sont pas au niveau de l’annuaire d’application.</span><span class="sxs-lookup"><span data-stu-id="27353-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="27353-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27353-160">See also</span></span>

- [<span data-ttu-id="27353-161">Schéma de fichier de configuration pour le cadre .NET</span><span class="sxs-lookup"><span data-stu-id="27353-161">Configuration file schema for the .NET Framework</span></span>](index.md)
