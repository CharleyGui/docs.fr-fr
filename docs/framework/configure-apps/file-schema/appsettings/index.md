---
title: Schéma des paramètres d’application
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: a67689bd9757f7586881fd910ef6103b1dffeab8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550447"
---
# <a name="app-settings-schema"></a><span data-ttu-id="31620-102">Schéma des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="31620-102">App Settings schema</span></span>

<span data-ttu-id="31620-103">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="31620-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| <span data-ttu-id="31620-104">Élément</span><span class="sxs-lookup"><span data-stu-id="31620-104">Element</span></span> | <span data-ttu-id="31620-105">Description</span><span class="sxs-lookup"><span data-stu-id="31620-105">Description</span></span> |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="31620-106">Contient **\<add>** des **\<clear>** **\<remove>** balises, et pour contrôler les paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="31620-106">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="31620-107">A un attribut **file** facultatif.</span><span class="sxs-lookup"><span data-stu-id="31620-107">Has an optional **file** attribute.</span></span> |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="31620-108">Définit un paramètre.</span><span class="sxs-lookup"><span data-stu-id="31620-108">Defines a setting.</span></span> <span data-ttu-id="31620-109">Enfant de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="31620-109">Child of **\<appSettings>**.</span></span> <span data-ttu-id="31620-110">Requiert des attributs **key** et **value**.</span><span class="sxs-lookup"><span data-stu-id="31620-110">Requires **key** and **value** attributes.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="31620-111">Efface tous les paramètres.</span><span class="sxs-lookup"><span data-stu-id="31620-111">Clears all settings.</span></span> <span data-ttu-id="31620-112">Enfant de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="31620-112">Child of **\<appSettings>**.</span></span> <span data-ttu-id="31620-113">N’a pas d’attributs.</span><span class="sxs-lookup"><span data-stu-id="31620-113">Has no attributes.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="31620-114">Supprime un paramètre.</span><span class="sxs-lookup"><span data-stu-id="31620-114">Removes a setting.</span></span> <span data-ttu-id="31620-115">Enfant de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="31620-115">Child of **\<appSettings>**.</span></span> <span data-ttu-id="31620-116">Exige un attribut **key**.</span><span class="sxs-lookup"><span data-stu-id="31620-116">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="31620-117">\<appSettings>, élément</span><span class="sxs-lookup"><span data-stu-id="31620-117">\<appSettings> element</span></span>

<span data-ttu-id="31620-118">Cet élément contient **\<add>** des **\<clear>** **\<remove>** balises, et pour contrôler les paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="31620-118">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="31620-119">Il définit un attribut facultatif pour **file**.</span><span class="sxs-lookup"><span data-stu-id="31620-119">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="31620-120">\<add>, élément</span><span class="sxs-lookup"><span data-stu-id="31620-120">\<add> element</span></span>

<span data-ttu-id="31620-121">Ajoute un paramètre d’application personnalisé en tant que paire nom/valeur à la collection de paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="31620-121">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="31620-122">Il définit les attributs pour **key** et **value**.</span><span class="sxs-lookup"><span data-stu-id="31620-122">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="31620-123">\<clear>, élément</span><span class="sxs-lookup"><span data-stu-id="31620-123">\<clear> element</span></span>

<span data-ttu-id="31620-124">Supprime toutes les références aux paramètres d’application personnalisés hérités et autorise uniquement les références qui sont ajoutées par **\<add>** les éléments qui suivent l' **\<clear>** élément.</span><span class="sxs-lookup"><span data-stu-id="31620-124">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="31620-125">Il ne définit aucun attribut.</span><span class="sxs-lookup"><span data-stu-id="31620-125">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="31620-126">\<remove>, élément</span><span class="sxs-lookup"><span data-stu-id="31620-126">\<remove> element</span></span>

<span data-ttu-id="31620-127">Supprime une référence à un paramètre d’application personnalisé hérité de la collection de paramètres d’application.</span><span class="sxs-lookup"><span data-stu-id="31620-127">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="31620-128">Il définit un attribut pour **key**.</span><span class="sxs-lookup"><span data-stu-id="31620-128">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="31620-129"> Exemple</span><span class="sxs-lookup"><span data-stu-id="31620-129">Example</span></span>

<span data-ttu-id="31620-130">L’exemple suivant montre un fichier de paramètres d’application externe (*custom.config*) qui définit un paramètre d’application personnalisé :</span><span class="sxs-lookup"><span data-stu-id="31620-130">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="31620-131">L’exemple suivant montre un fichier de configuration d’application qui consomme le paramètre dans le fichier de paramètres externes et définit un paramètre d’application qui lui est propre :</span><span class="sxs-lookup"><span data-stu-id="31620-131">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="31620-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31620-132">See also</span></span>

- [<span data-ttu-id="31620-133">Vue d'ensemble des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="31620-133">Application Settings Overview</span></span>](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [<span data-ttu-id="31620-134">Architecture des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="31620-134">Application Settings Architecture</span></span>](/dotnet/desktop/winforms/advanced/application-settings-architecture)
