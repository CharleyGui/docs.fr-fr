---
title: Configuration de votre application
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 6fc33e7b114bb78f823575a2b456d601ae75db94
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937645"
---
# <a name="configuring-your-application"></a>Configuration de votre application
Windows Communication Foundation (WCF) utilise le système de configuration .NET et vous permet de configurer des services à la fois sur l’ordinateur et sur l’étendue de l’application.  
  
 Les paramètres de configuration définis par WCF se trouvent dans le groupe de sections `<system.serviceModel>`. Pour plus d’informations sur la configuration d’un service WCF, consultez les rubriques suivantes :  
  
- [Configuration des services](../configuring-services.md)  
  
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Les paramètres de configuration définis par l'application sont définis dans le groupe de sections `<appSettings>`. Pour plus d’informations sur les paramètres d’application dans les fichiers de configuration .NET, consultez [\<appSettings >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)).  
  
## <a name="using-the-configuration-editor"></a>Utilisation de l'Éditeur de configuration  
 L' [outil Éditeur de configuration WCF (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md) permet aux administrateurs et aux développeurs de créer et de modifier des paramètres de configuration pour les services WCF à l’aide d’une interface utilisateur graphique. Avec cet outil, vous pouvez gérer les paramètres des liaisons, comportements, services et diagnostics WCF sans modifier directement les fichiers de configuration XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Modification des fichiers de configuration dans Visual Studio  
 Pour modifier le fichier de configuration d’un projet de service WCF dans Visual Studio, cliquez dessus avec le bouton droit dans **Explorateur de solutions** et choisissez l’élément de menu contextuel **modifier la configuration WCF** . Cela lance l' [outil Éditeur de configuration (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
> Si vous modifiez le fichier de configuration d’un projet de service Web WCF dans Visual Studio en cliquant dessus avec le bouton droit dans **Explorateur de solutions**, vous remarquerez que l’élément de menu contextuel **modifier la configuration WCF** est manquant. Pour contourner ce problème, cliquez sur le menu **Outils** , puis choisissez **éditeur de configuration de service WCF**. Après cela, vous pouvez cliquer avec le bouton droit sur un fichier de configuration et utiliser l’élément de menu contextuel **modifier la configuration WCF** .  
  
## <a name="see-also"></a>Voir aussi

- [Outil Éditeur de configuration (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)
- [Configuration des services](../configuring-services.md)
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
