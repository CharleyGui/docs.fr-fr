---
title: 'Comment : écrire les services par programmation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: 5637d569ad5261bff6865af4ab2ed8b7631d2d38
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053557"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="aebd0-102">Comment : écrire les services par programmation</span><span class="sxs-lookup"><span data-stu-id="aebd0-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="aebd0-103">Si vous choisissez de ne pas utiliser le modèle de projet Service Windows, vous pouvez écrire vos propres services en configurant vous-même l’héritage et d’autres éléments d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="aebd0-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="aebd0-104">Quand vous créez un service par programmation, vous devez effectuer plusieurs étapes qui sont normalement gérées pour vous par le modèle :</span><span class="sxs-lookup"><span data-stu-id="aebd0-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
- <span data-ttu-id="aebd0-105">Vous devez configurer votre classe de service pour qu’elle hérite de la classe <xref:System.ServiceProcess.ServiceBase>.</span><span class="sxs-lookup"><span data-stu-id="aebd0-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
- <span data-ttu-id="aebd0-106">Vous devez créer une méthode `Main` pour votre projet de service qui définit les services à exécuter et appelle la méthode <xref:System.ServiceProcess.ServiceBase.Run%2A> sur ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="aebd0-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
- <span data-ttu-id="aebd0-107">Vous devez substituer les procédures <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A> et indiquer le code que vous souhaitez qu’elles exécutent.</span><span class="sxs-lookup"><span data-stu-id="aebd0-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="aebd0-108">Pour écrire un service par programmation</span><span class="sxs-lookup"><span data-stu-id="aebd0-108">To write a service programmatically</span></span>  
  
1. <span data-ttu-id="aebd0-109">Créez un projet vide, puis une référence aux espaces de noms nécessaires. Pour cela, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="aebd0-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1. <span data-ttu-id="aebd0-110">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références**, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="aebd0-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2. <span data-ttu-id="aebd0-111">Sous l’onglet **.NET Framework**, faites défiler jusqu’à **System.dll**, puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="aebd0-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3. <span data-ttu-id="aebd0-112">Faites défiler jusqu’à **System.Diagnostics.dll**, puis cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="aebd0-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4. <span data-ttu-id="aebd0-113">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aebd0-113">Click **OK**.</span></span>  
  
2. <span data-ttu-id="aebd0-114">Ajoutez une classe et configurez-la pour qu’elle hérite de <xref:System.ServiceProcess.ServiceBase> :</span><span class="sxs-lookup"><span data-stu-id="aebd0-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. <span data-ttu-id="aebd0-115">Ajoutez le code suivant pour configurer votre classe de service :</span><span class="sxs-lookup"><span data-stu-id="aebd0-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. <span data-ttu-id="aebd0-116">Créez une méthode `Main` pour votre classe, et utilisez-la pour définir le service qui sera contenu dans votre classe. `userService1` est le nom de la classe :</span><span class="sxs-lookup"><span data-stu-id="aebd0-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. <span data-ttu-id="aebd0-117">Substituez la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, et définissez le traitement qui doit se produire au démarrage de votre service.</span><span class="sxs-lookup"><span data-stu-id="aebd0-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. <span data-ttu-id="aebd0-118">Substituez les autres méthodes pour lesquelles vous souhaitez définir un traitement personnalisé, et écrivez le code nécessaire pour déterminer les actions que le service doit prendre dans chaque cas.</span><span class="sxs-lookup"><span data-stu-id="aebd0-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7. <span data-ttu-id="aebd0-119">Ajoutez les programmes d'installation nécessaires à votre application de service.</span><span class="sxs-lookup"><span data-stu-id="aebd0-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="aebd0-120">Pour plus d’informations, consultez [Guide pratique pour ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="aebd0-120">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
8. <span data-ttu-id="aebd0-121">Générez votre projet en sélectionnant **Générer la solution** dans le menu **Générer**.</span><span class="sxs-lookup"><span data-stu-id="aebd0-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="aebd0-122">N'appuyez pas sur la touche F5 pour exécuter votre projet : vous ne pouvez pas exécuter un projet de service de cette manière.</span><span class="sxs-lookup"><span data-stu-id="aebd0-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="aebd0-123">Créez un projet d’installation et les actions personnalisées pour installer votre service.</span><span class="sxs-lookup"><span data-stu-id="aebd0-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="aebd0-124">Pour obtenir un exemple, consultez [Procédure pas à pas : création d’une application de service Windows dans le Concepteur de composants](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="aebd0-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="aebd0-125">Installez le service.</span><span class="sxs-lookup"><span data-stu-id="aebd0-125">Install the service.</span></span> <span data-ttu-id="aebd0-126">Pour plus d'informations, consultez [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="aebd0-126">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aebd0-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aebd0-127">See also</span></span>

- [<span data-ttu-id="aebd0-128">Présentation des applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="aebd0-128">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="aebd0-129">Guide pratique pour créer des services Windows</span><span class="sxs-lookup"><span data-stu-id="aebd0-129">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="aebd0-130">Comment : ajouter des programmes d'installation à votre application de service</span><span class="sxs-lookup"><span data-stu-id="aebd0-130">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="aebd0-131">Comment : enregistrer des informations relatives aux services</span><span class="sxs-lookup"><span data-stu-id="aebd0-131">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="aebd0-132">Procédure pas à pas : création d’une application de service Windows dans le Concepteur de composants</span><span class="sxs-lookup"><span data-stu-id="aebd0-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
