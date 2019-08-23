---
title: Schéma des paramètres de l’application
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 89a08434332b0242fe57e9dcaa3b3ebcc5692d06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927759"
---
# <a name="application-settings-schema"></a><span data-ttu-id="eed7a-102">Schéma des paramètres de l’application</span><span class="sxs-lookup"><span data-stu-id="eed7a-102">Application Settings schema</span></span>

<span data-ttu-id="eed7a-103">Les paramètres d’application permettent à une application de Windows Forms ou ASP.NET de stocker et d’extraire des paramètres de portée application et de portée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="eed7a-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="eed7a-104">Dans ce contexte, un *paramètre* est une information qui peut être spécifique à l’application ou spécifique à l’utilisateur actuel (tout ce qui provient d’une chaîne de connexion de base de données à la taille de fenêtre par défaut préférée de l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="eed7a-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="eed7a-105">Par défaut, les paramètres d’application d’une application Windows Forms <xref:System.Configuration.LocalFileSettingsProvider> utilisent la classe, qui utilise le système de configuration .net pour stocker les paramètres dans un fichier de configuration XML.</span><span class="sxs-lookup"><span data-stu-id="eed7a-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="eed7a-106">Pour plus d’informations sur les fichiers utilisés par les paramètres d’application, consultez [architecture des paramètres d’application](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="eed7a-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="eed7a-107">Les paramètres d’application définissent les éléments suivants dans le cadre des fichiers de configuration qu’il utilise.</span><span class="sxs-lookup"><span data-stu-id="eed7a-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="eed7a-108">Élément</span><span class="sxs-lookup"><span data-stu-id="eed7a-108">Element</span></span>                    | <span data-ttu-id="eed7a-109">Description</span><span class="sxs-lookup"><span data-stu-id="eed7a-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="eed7a-110">**\<applicationSettings>**</span><span class="sxs-lookup"><span data-stu-id="eed7a-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="eed7a-111">Contient toutes  **\<** les balises de > de paramètres spécifiques à l’application.</span><span class="sxs-lookup"><span data-stu-id="eed7a-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="eed7a-112">**\<userSettings>**</span><span class="sxs-lookup"><span data-stu-id="eed7a-112">**\<userSettings>**</span></span>        | <span data-ttu-id="eed7a-113">Contient toutes  **\<** les balises de > de paramètres spécifiques à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="eed7a-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="eed7a-114">**\<setting>**</span><span class="sxs-lookup"><span data-stu-id="eed7a-114">**\<setting>**</span></span>             | <span data-ttu-id="eed7a-115">Définit un paramètre.</span><span class="sxs-lookup"><span data-stu-id="eed7a-115">Defines a setting.</span></span> <span data-ttu-id="eed7a-116">Enfant de la  **\<> ApplicationSettings** ou  **\<de l' > UserSettings**.</span><span class="sxs-lookup"><span data-stu-id="eed7a-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="eed7a-117">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="eed7a-117">**\<value>**</span></span>               | <span data-ttu-id="eed7a-118">Définit la valeur d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="eed7a-118">Defines a setting's value.</span></span> <span data-ttu-id="eed7a-119">Enfant du  **\<paramètre >** .</span><span class="sxs-lookup"><span data-stu-id="eed7a-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="eed7a-120">\<élément > applicationSettings</span><span class="sxs-lookup"><span data-stu-id="eed7a-120">\<applicationSettings> element</span></span>

<span data-ttu-id="eed7a-121">Cet élément contient tous les  **\<paramètres >** balises spécifiques à une instance de l’application sur un ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="eed7a-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="eed7a-122">Il ne définit aucun attribut.</span><span class="sxs-lookup"><span data-stu-id="eed7a-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="eed7a-123">\<élément > userSettings</span><span class="sxs-lookup"><span data-stu-id="eed7a-123">\<userSettings> element</span></span>

<span data-ttu-id="eed7a-124">Cet élément contient tous les  **\<paramètres >** balises spécifiques à l’utilisateur qui utilise actuellement l’application.</span><span class="sxs-lookup"><span data-stu-id="eed7a-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="eed7a-125">Il ne définit aucun attribut.</span><span class="sxs-lookup"><span data-stu-id="eed7a-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="eed7a-126">\<définition de l’élément ></span><span class="sxs-lookup"><span data-stu-id="eed7a-126">\<setting> element</span></span>

<span data-ttu-id="eed7a-127">Cet élément définit un paramètre.</span><span class="sxs-lookup"><span data-stu-id="eed7a-127">This element defines a setting.</span></span> <span data-ttu-id="eed7a-128">Il a les attributs suivants.</span><span class="sxs-lookup"><span data-stu-id="eed7a-128">It has the following attributes.</span></span>

| <span data-ttu-id="eed7a-129">Attribut</span><span class="sxs-lookup"><span data-stu-id="eed7a-129">Attribute</span></span>        | <span data-ttu-id="eed7a-130">Description</span><span class="sxs-lookup"><span data-stu-id="eed7a-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="eed7a-131">**name**</span><span class="sxs-lookup"><span data-stu-id="eed7a-131">**name**</span></span>         | <span data-ttu-id="eed7a-132">Requis.</span><span class="sxs-lookup"><span data-stu-id="eed7a-132">Required.</span></span> <span data-ttu-id="eed7a-133">ID unique du paramètre.</span><span class="sxs-lookup"><span data-stu-id="eed7a-133">The unique ID of the setting.</span></span> <span data-ttu-id="eed7a-134">Les paramètres créés par le biais de Visual Studio sont `ProjectName.Properties.Settings`enregistrés avec le nom.</span><span class="sxs-lookup"><span data-stu-id="eed7a-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="eed7a-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="eed7a-135">**serializedAs**</span></span> | <span data-ttu-id="eed7a-136">Requis.</span><span class="sxs-lookup"><span data-stu-id="eed7a-136">Required.</span></span> <span data-ttu-id="eed7a-137">Format à utiliser pour sérialiser la valeur dans le texte.</span><span class="sxs-lookup"><span data-stu-id="eed7a-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="eed7a-138">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="eed7a-138">Valid values are:</span></span><br><br><span data-ttu-id="eed7a-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="eed7a-139">- `string`.</span></span> <span data-ttu-id="eed7a-140">La valeur est sérialisée sous forme de chaîne à <xref:System.ComponentModel.TypeConverter>l’aide d’un.</span><span class="sxs-lookup"><span data-stu-id="eed7a-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="eed7a-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="eed7a-141">- `xml`.</span></span> <span data-ttu-id="eed7a-142">La valeur est sérialisée à l’aide de la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="eed7a-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="eed7a-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="eed7a-143">- `binary`.</span></span> <span data-ttu-id="eed7a-144">La valeur est sérialisée comme binaire encodé en texte à l’aide de la sérialisation binaire.</span><span class="sxs-lookup"><span data-stu-id="eed7a-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="eed7a-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="eed7a-145">- `custom`.</span></span> <span data-ttu-id="eed7a-146">Le fournisseur de paramètres a une connaissance inhérente de ce paramètre et le sérialise et le désérialise.</span><span class="sxs-lookup"><span data-stu-id="eed7a-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="eed7a-147">\<élément de > de valeur</span><span class="sxs-lookup"><span data-stu-id="eed7a-147">\<value> element</span></span>

<span data-ttu-id="eed7a-148">Cet élément contient la valeur d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="eed7a-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="eed7a-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="eed7a-149">Example</span></span>

<span data-ttu-id="eed7a-150">L’exemple suivant montre un fichier de paramètres d’application qui définit deux paramètres de portée application et deux paramètres de portée utilisateur:</span><span class="sxs-lookup"><span data-stu-id="eed7a-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eed7a-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eed7a-151">See also</span></span>

- [<span data-ttu-id="eed7a-152">Vue d'ensemble des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="eed7a-152">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="eed7a-153">Architecture des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="eed7a-153">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
