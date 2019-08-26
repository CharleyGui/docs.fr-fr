---
title: 'Procédure : poursuivre un service Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
author: ghogen
ms.openlocfilehash: c9a783c0e7df39381ad1d9a8fedd7419605fd241
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935540"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="f2dfe-102">Procédure : poursuivre un service Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2dfe-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="f2dfe-103">Cet exemple utilise le composant <xref:System.ServiceProcess.ServiceController> pour continuer le service d’administration IIS sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2dfe-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="f2dfe-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="f2dfe-105">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="f2dfe-106">Dans le sélecteur d’extraits de code, il se trouve dans **Système d’exploitation Windows > Services Windows**.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="f2dfe-107">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="f2dfe-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f2dfe-108">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f2dfe-108">Compiling the Code</span></span>  
 <span data-ttu-id="f2dfe-109">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="f2dfe-109">This example requires:</span></span>  
  
- <span data-ttu-id="f2dfe-110">Une référence de projet à System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="f2dfe-111">Un accès aux membres de l’espace de noms <xref:System.ServiceProcess>.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="f2dfe-112">Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="f2dfe-113">Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="f2dfe-113">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f2dfe-114">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="f2dfe-114">Robust Programming</span></span>  
 <span data-ttu-id="f2dfe-115">La propriété <xref:System.ServiceProcess.ServiceController.MachineName%2A> de la classe <xref:System.ServiceProcess.ServiceController> est l’ordinateur local par défaut.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="f2dfe-116">Pour référencer des services Windows sur un autre ordinateur, remplacez la propriété <xref:System.ServiceProcess.ServiceController.MachineName%2A> par le nom de cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="f2dfe-117">Vous pouvez appeler la méthode <xref:System.ServiceProcess.ServiceController.Continue%2A> sur un service seulement si l’état du contrôleur de service est <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="f2dfe-118">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="f2dfe-119">Le service ne peut pas être repris.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-119">The service cannot be resumed.</span></span> <span data-ttu-id="f2dfe-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="f2dfe-120">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="f2dfe-121">Une erreur s'est produite lors de l'accès à une API système.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="f2dfe-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="f2dfe-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f2dfe-123">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f2dfe-123">.NET Framework Security</span></span>  
 <span data-ttu-id="f2dfe-124">Vous pouvez restreindre le contrôle des services sur l’ordinateur à l’aide de l’énumération <xref:System.ServiceProcess.ServiceControllerPermissionAccess>, qui permet de définir des autorisations dans la classe <xref:System.ServiceProcess.ServiceControllerPermission>.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="f2dfe-125">Vous pouvez restreindre l’accès aux informations de service à l’aide de l’énumération <xref:System.Security.Permissions.PermissionState>, qui permet de définir des autorisations dans la classe <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="f2dfe-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2dfe-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2dfe-126">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [<span data-ttu-id="f2dfe-127">Guide pratique pour interrompre un service Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2dfe-127">How to: Pause a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
