---
title: 'Procédure : interrompre un service Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
author: ghogen
ms.openlocfilehash: 166eda4a9348188fa6e5048fd3ce41645cde4816
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053597"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="b85a2-102">Procédure : interrompre un service Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b85a2-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="b85a2-103">Cet exemple utilise le composant <xref:System.ServiceProcess.ServiceController> pour interrompre le service d’administration IIS sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b85a2-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b85a2-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b85a2-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="b85a2-105">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="b85a2-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="b85a2-106">Dans le sélecteur d’extraits de code, il se trouve dans **Système d’exploitation Windows > Services Windows**.</span><span class="sxs-lookup"><span data-stu-id="b85a2-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="b85a2-107">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="b85a2-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b85a2-108">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b85a2-108">Compiling the Code</span></span>  
 <span data-ttu-id="b85a2-109">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="b85a2-109">This example requires:</span></span>  
  
- <span data-ttu-id="b85a2-110">Une référence de projet à System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="b85a2-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="b85a2-111">Un accès aux membres de l’espace de noms <xref:System.ServiceProcess>.</span><span class="sxs-lookup"><span data-stu-id="b85a2-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="b85a2-112">Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code.</span><span class="sxs-lookup"><span data-stu-id="b85a2-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="b85a2-113">Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="b85a2-113">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b85a2-114">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="b85a2-114">Robust Programming</span></span>  
 <span data-ttu-id="b85a2-115">La propriété <xref:System.ServiceProcess.ServiceController.MachineName%2A> de la classe <xref:System.ServiceProcess.ServiceController> est l’ordinateur local par défaut.</span><span class="sxs-lookup"><span data-stu-id="b85a2-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="b85a2-116">Pour référencer des services Windows sur un autre ordinateur, remplacez la propriété <xref:System.ServiceProcess.ServiceController.MachineName%2A> par le nom de cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b85a2-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="b85a2-117">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="b85a2-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b85a2-118">Le service ne peut pas être suspendu.</span><span class="sxs-lookup"><span data-stu-id="b85a2-118">The service cannot be paused.</span></span> <span data-ttu-id="b85a2-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="b85a2-119">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="b85a2-120">Une erreur s'est produite lors de l'accès à une API système.</span><span class="sxs-lookup"><span data-stu-id="b85a2-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="b85a2-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="b85a2-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b85a2-122">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b85a2-122">.NET Framework Security</span></span>  
 <span data-ttu-id="b85a2-123">Vous pouvez restreindre le contrôle des services sur l’ordinateur à l’aide de <xref:System.ServiceProcess.ServiceControllerPermissionAccess>, qui permet de définir des autorisations dans <xref:System.ServiceProcess.ServiceControllerPermission>.</span><span class="sxs-lookup"><span data-stu-id="b85a2-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="b85a2-124">Vous pouvez restreindre l’accès aux informations de service à l’aide de <xref:System.Security.Permissions.PermissionState>, qui permet de définir des autorisations dans <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="b85a2-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b85a2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b85a2-125">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="b85a2-126">Guide pratique pour poursuivre un service Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b85a2-126">How to: Continue a Windows Service (Visual Basic)</span></span>](how-to-continue-a-windows-service-visual-basic.md)
