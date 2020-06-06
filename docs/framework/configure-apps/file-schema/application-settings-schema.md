---
title: Schéma des paramètres de l’application
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81242827"
---
# <a name="application-settings-schema"></a><span data-ttu-id="90002-102">Schéma des paramètres de l’application</span><span class="sxs-lookup"><span data-stu-id="90002-102">Application Settings schema</span></span>

<span data-ttu-id="90002-103">Les paramètres d’application permettent à une application de Windows Forms ou ASP.NET de stocker et d’extraire des paramètres de portée application et de portée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="90002-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="90002-104">Dans ce contexte, un *paramètre* est une information qui peut être spécifique à l’application ou spécifique à l’utilisateur actuel (tout ce qui provient d’une chaîne de connexion de base de données à la taille de fenêtre par défaut préférée de l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="90002-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="90002-105">Par défaut, les paramètres d’application d’une application Windows Forms utilisent la <xref:System.Configuration.LocalFileSettingsProvider> classe, qui utilise le système de configuration .net pour stocker les paramètres dans un fichier de configuration XML.</span><span class="sxs-lookup"><span data-stu-id="90002-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="90002-106">Pour plus d’informations sur les fichiers utilisés par les paramètres d’application, consultez [architecture des paramètres d’application](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="90002-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="90002-107">Les paramètres d’application définissent les éléments suivants dans le cadre des fichiers de configuration qu’il utilise.</span><span class="sxs-lookup"><span data-stu-id="90002-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="90002-108">Élément</span><span class="sxs-lookup"><span data-stu-id="90002-108">Element</span></span>                    | <span data-ttu-id="90002-109">Description</span><span class="sxs-lookup"><span data-stu-id="90002-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | <span data-ttu-id="90002-110">Contient toutes les **\<setting>** balises spécifiques à l’application.</span><span class="sxs-lookup"><span data-stu-id="90002-110">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| **\<userSettings>**        | <span data-ttu-id="90002-111">Contient toutes les **\<setting>** balises spécifiques à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="90002-111">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| **\<setting>**             | <span data-ttu-id="90002-112">Définit un paramètre.</span><span class="sxs-lookup"><span data-stu-id="90002-112">Defines a setting.</span></span> <span data-ttu-id="90002-113">Enfant de **\<applicationSettings>** ou **\<userSettings>** .</span><span class="sxs-lookup"><span data-stu-id="90002-113">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| **\<value>**               | <span data-ttu-id="90002-114">Définit la valeur d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="90002-114">Defines a setting's value.</span></span> <span data-ttu-id="90002-115">Enfant de **\<setting>** .</span><span class="sxs-lookup"><span data-stu-id="90002-115">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="90002-116">\<applicationSettings>, élément</span><span class="sxs-lookup"><span data-stu-id="90002-116">\<applicationSettings> element</span></span>

<span data-ttu-id="90002-117">Cet élément contient toutes les **\<setting>** balises qui sont spécifiques à une instance de l’application sur un ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="90002-117">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="90002-118">Il ne définit aucun attribut.</span><span class="sxs-lookup"><span data-stu-id="90002-118">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="90002-119">\<userSettings>, élément</span><span class="sxs-lookup"><span data-stu-id="90002-119">\<userSettings> element</span></span>

<span data-ttu-id="90002-120">Cet élément contient toutes les **\<setting>** balises qui sont spécifiques à l’utilisateur qui utilise actuellement l’application.</span><span class="sxs-lookup"><span data-stu-id="90002-120">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="90002-121">Il ne définit aucun attribut.</span><span class="sxs-lookup"><span data-stu-id="90002-121">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="90002-122">\<setting>, élément</span><span class="sxs-lookup"><span data-stu-id="90002-122">\<setting> element</span></span>

<span data-ttu-id="90002-123">Cet élément définit un paramètre.</span><span class="sxs-lookup"><span data-stu-id="90002-123">This element defines a setting.</span></span> <span data-ttu-id="90002-124">Il a les attributs suivants.</span><span class="sxs-lookup"><span data-stu-id="90002-124">It has the following attributes.</span></span>

| <span data-ttu-id="90002-125">Attribut</span><span class="sxs-lookup"><span data-stu-id="90002-125">Attribute</span></span>        | <span data-ttu-id="90002-126">Description</span><span class="sxs-lookup"><span data-stu-id="90002-126">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="90002-127">**name**</span><span class="sxs-lookup"><span data-stu-id="90002-127">**name**</span></span>         | <span data-ttu-id="90002-128">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="90002-128">Required.</span></span> <span data-ttu-id="90002-129">ID unique du paramètre.</span><span class="sxs-lookup"><span data-stu-id="90002-129">The unique ID of the setting.</span></span> <span data-ttu-id="90002-130">Les paramètres créés par le biais de Visual Studio sont enregistrés avec le nom `ProjectName.Properties.Settings` .</span><span class="sxs-lookup"><span data-stu-id="90002-130">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="90002-131">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="90002-131">**serializeAs**</span></span> | <span data-ttu-id="90002-132">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="90002-132">Required.</span></span> <span data-ttu-id="90002-133">Format à utiliser pour sérialiser la valeur dans le texte.</span><span class="sxs-lookup"><span data-stu-id="90002-133">The format to use for serializing the value to text.</span></span> <span data-ttu-id="90002-134">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="90002-134">Valid values are:</span></span><br><br><span data-ttu-id="90002-135">- `string`.</span><span class="sxs-lookup"><span data-stu-id="90002-135">- `string`.</span></span> <span data-ttu-id="90002-136">La valeur est sérialisée sous forme de chaîne à l’aide d’un <xref:System.ComponentModel.TypeConverter> .</span><span class="sxs-lookup"><span data-stu-id="90002-136">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="90002-137">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="90002-137">- `xml`.</span></span> <span data-ttu-id="90002-138">La valeur est sérialisée à l’aide de la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="90002-138">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="90002-139">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="90002-139">- `binary`.</span></span> <span data-ttu-id="90002-140">La valeur est sérialisée comme binaire encodé en texte à l’aide de la sérialisation binaire.</span><span class="sxs-lookup"><span data-stu-id="90002-140">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="90002-141">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="90002-141">- `custom`.</span></span> <span data-ttu-id="90002-142">Le fournisseur de paramètres a une connaissance inhérente de ce paramètre et le sérialise et le désérialise.</span><span class="sxs-lookup"><span data-stu-id="90002-142">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="90002-143">\<value>, élément</span><span class="sxs-lookup"><span data-stu-id="90002-143">\<value> element</span></span>

<span data-ttu-id="90002-144">Cet élément contient la valeur d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="90002-144">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="90002-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="90002-145">Example</span></span>

<span data-ttu-id="90002-146">L’exemple suivant montre un fichier de paramètres d’application qui définit deux paramètres de portée application et deux paramètres de portée utilisateur :</span><span class="sxs-lookup"><span data-stu-id="90002-146">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="90002-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90002-147">See also</span></span>

- [<span data-ttu-id="90002-148">Vue d’ensemble des paramètres d’application</span><span class="sxs-lookup"><span data-stu-id="90002-148">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="90002-149">Application Settings Architecture</span><span class="sxs-lookup"><span data-stu-id="90002-149">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
