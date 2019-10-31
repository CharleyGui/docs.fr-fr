---
title: Schéma des paramètres d’application
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b931b76aa09b3f62fbd799990975268af4f7293
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119220"
---
# <a name="app-settings-schema"></a><span data-ttu-id="d038b-102">Schéma des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="d038b-102">App Settings schema</span></span>

<span data-ttu-id="d038b-103">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="d038b-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="d038b-104">[ **\<configuration>** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d038b-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="d038b-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d038b-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="d038b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<add>** ](add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="d038b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="d038b-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clear>** ](clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="d038b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="d038b-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<remove>** ](remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="d038b-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="d038b-109">Élément</span><span class="sxs-lookup"><span data-stu-id="d038b-109">Element</span></span> | <span data-ttu-id="d038b-110">Description</span><span class="sxs-lookup"><span data-stu-id="d038b-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="d038b-111"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="d038b-111">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="d038b-112">Contient des balises **\<add>** , **\<clear>** et **\<remove>** pour contrôler les paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="d038b-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="d038b-113">A un attribut **file** facultatif.</span><span class="sxs-lookup"><span data-stu-id="d038b-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="d038b-114"> **\<add>** </span><span class="sxs-lookup"><span data-stu-id="d038b-114">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="d038b-115">Définit un paramètre.</span><span class="sxs-lookup"><span data-stu-id="d038b-115">Defines a setting.</span></span> <span data-ttu-id="d038b-116">Enfant de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="d038b-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="d038b-117">Requiert des attributs **key** et **value**.</span><span class="sxs-lookup"><span data-stu-id="d038b-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="d038b-118"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="d038b-118">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="d038b-119">Efface tous les paramètres.</span><span class="sxs-lookup"><span data-stu-id="d038b-119">Clears all settings.</span></span> <span data-ttu-id="d038b-120">Enfant de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="d038b-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="d038b-121">N’a pas d’attributs.</span><span class="sxs-lookup"><span data-stu-id="d038b-121">Has no attributes.</span></span> |
| [<span data-ttu-id="d038b-122"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="d038b-122">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="d038b-123">Supprime un paramètre.</span><span class="sxs-lookup"><span data-stu-id="d038b-123">Removes a setting.</span></span> <span data-ttu-id="d038b-124">Enfant de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="d038b-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="d038b-125">Exige un attribut **key**.</span><span class="sxs-lookup"><span data-stu-id="d038b-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="d038b-126">\<appSettings>, élément</span><span class="sxs-lookup"><span data-stu-id="d038b-126">\<appSettings> element</span></span>

<span data-ttu-id="d038b-127">Cet élément contient des balises **\<add>** , **\<clear>** et **\<remove>** pour contrôler les paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="d038b-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="d038b-128">Il définit un attribut facultatif pour **file**.</span><span class="sxs-lookup"><span data-stu-id="d038b-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="d038b-129">\<add>, élément</span><span class="sxs-lookup"><span data-stu-id="d038b-129">\<add> element</span></span>

<span data-ttu-id="d038b-130">Ajoute un paramètre d’application personnalisé en tant que paire nom/valeur à la collection de paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="d038b-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="d038b-131">Il définit les attributs pour **key** et **value**.</span><span class="sxs-lookup"><span data-stu-id="d038b-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="d038b-132">\<clear>, élément</span><span class="sxs-lookup"><span data-stu-id="d038b-132">\<clear> element</span></span>

<span data-ttu-id="d038b-133">Supprime toutes les références aux paramètres d’application personnalisés hérités et autorise uniquement les références ajoutées par les éléments **\<add>** suivant l’élément **\<clear>** .</span><span class="sxs-lookup"><span data-stu-id="d038b-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="d038b-134">Il ne définit aucun attribut.</span><span class="sxs-lookup"><span data-stu-id="d038b-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="d038b-135">\<remove>, élément</span><span class="sxs-lookup"><span data-stu-id="d038b-135">\<remove> element</span></span>

<span data-ttu-id="d038b-136">Supprime une référence à un paramètre d’application personnalisé hérité de la collection de paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="d038b-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="d038b-137">Il définit un attribut pour **key**.</span><span class="sxs-lookup"><span data-stu-id="d038b-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="d038b-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="d038b-138">Example</span></span>

<span data-ttu-id="d038b-139">L’exemple suivant montre un fichier de paramètres d’application externe (*custom.config*) qui définit un paramètre d’application personnalisé :</span><span class="sxs-lookup"><span data-stu-id="d038b-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="d038b-140">L’exemple suivant montre un fichier de configuration d’application qui consomme le paramètre dans le fichier de paramètres externes et définit un paramètre d’application qui lui est propre :</span><span class="sxs-lookup"><span data-stu-id="d038b-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="d038b-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d038b-141">See also</span></span>

- [<span data-ttu-id="d038b-142">Vue d'ensemble des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="d038b-142">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="d038b-143">Architecture des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="d038b-143">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
