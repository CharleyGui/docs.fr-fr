---
title: Configuration de votre application
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 04ddce4755ce30b7d46c3bd54024af08361d96ad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536079"
---
# <a name="configuring-your-application"></a><span data-ttu-id="9e405-102">Configuration de votre application</span><span class="sxs-lookup"><span data-stu-id="9e405-102">Configuring Your Application</span></span>
<span data-ttu-id="9e405-103">Windows Communication Foundation (WCF) utilise le système de configuration .NET et vous permet de configurer des services à la fois sur l’ordinateur et sur l’étendue de l’application.</span><span class="sxs-lookup"><span data-stu-id="9e405-103">Windows Communication Foundation (WCF) uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="9e405-104">Les paramètres de configuration définis par WCF se trouvent dans le `<system.serviceModel>` groupe de sections.</span><span class="sxs-lookup"><span data-stu-id="9e405-104">Configuration settings defined by WCF are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="9e405-105">Pour plus d’informations sur la configuration d’un service WCF, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="9e405-105">For more information about how to configure a WCF service, see the following topics:</span></span>  
  
- [<span data-ttu-id="9e405-106">Configuration des services</span><span class="sxs-lookup"><span data-stu-id="9e405-106">Configuring Services</span></span>](../configuring-services.md)  
  
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="9e405-107">Les paramètres de configuration définis par l'application sont définis dans le groupe de sections `<appSettings>`.</span><span class="sxs-lookup"><span data-stu-id="9e405-107">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="9e405-108">Pour plus d’informations sur les paramètres d’application dans les fichiers de configuration .NET, consultez [\<appSettings>](/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="9e405-108">For more information about application settings in .NET configuration files, see [\<appSettings>](/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="9e405-109">Utilisation de l'Éditeur de configuration</span><span class="sxs-lookup"><span data-stu-id="9e405-109">Using the Configuration Editor</span></span>  
 <span data-ttu-id="9e405-110">L’outil de l' [éditeur de configuration WCF (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) permet aux administrateurs et aux développeurs de créer et de modifier des paramètres de configuration pour les services WCF à l’aide d’une interface utilisateur graphique.</span><span class="sxs-lookup"><span data-stu-id="9e405-110">The WCF [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="9e405-111">Avec cet outil, vous pouvez gérer les paramètres des liaisons, comportements, services et diagnostics WCF sans modifier directement les fichiers de configuration XML.</span><span class="sxs-lookup"><span data-stu-id="9e405-111">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="9e405-112">Modification des fichiers de configuration dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9e405-112">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="9e405-113">Pour modifier le fichier de configuration d’un projet de service WCF dans Visual Studio, cliquez dessus avec le bouton droit dans **Explorateur de solutions** et choisissez l’élément de menu contextuel **modifier la configuration WCF** .</span><span class="sxs-lookup"><span data-stu-id="9e405-113">To edit the configuration file of a WCF service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="9e405-114">Cela lance l' [outil Éditeur de configuration (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9e405-114">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e405-115">Si vous modifiez le fichier de configuration d’un projet de service Web WCF dans Visual Studio en cliquant dessus avec le bouton droit dans **Explorateur de solutions**, vous remarquerez que l’élément de menu contextuel **modifier la configuration WCF** est manquant.</span><span class="sxs-lookup"><span data-stu-id="9e405-115">If you edit the configuration file of a WCF Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="9e405-116">Pour contourner ce problème, cliquez sur le menu **Outils** , puis choisissez **éditeur de configuration de service WCF**.</span><span class="sxs-lookup"><span data-stu-id="9e405-116">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="9e405-117">Après cela, vous pouvez cliquer avec le bouton droit sur un fichier de configuration et utiliser l’élément de menu contextuel **modifier la configuration WCF** .</span><span class="sxs-lookup"><span data-stu-id="9e405-117">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e405-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e405-118">See also</span></span>

- [<span data-ttu-id="9e405-119">Outil Éditeur de configuration (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="9e405-119">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../configuration-editor-tool-svcconfigeditor-exe.md)
- [<span data-ttu-id="9e405-120">Configuration des services</span><span class="sxs-lookup"><span data-stu-id="9e405-120">Configuring Services</span></span>](../configuring-services.md)
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
