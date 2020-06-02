---
title: Emprunt et restauration d'identité
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: dbfd71830ace1eb8af9f55f06c9ce35c32d592bb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288015"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="57c74-102">Emprunt et restauration d'identité</span><span class="sxs-lookup"><span data-stu-id="57c74-102">Impersonating and Reverting</span></span>
<span data-ttu-id="57c74-103">Parfois, vous devez obtenir un jeton de compte Windows pour emprunter l’identité d’un compte Windows.</span><span class="sxs-lookup"><span data-stu-id="57c74-103">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="57c74-104">Par exemple, votre application ASP.NET peut devoir agir pour le compte de plusieurs utilisateurs à des moments différents.</span><span class="sxs-lookup"><span data-stu-id="57c74-104">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="57c74-105">Votre application peut accepter un jeton représentant un administrateur à partir d’Internet Information Services (IIS), emprunter l’identité de cet utilisateur, effectuer une opération et revenir à l’identité précédente.</span><span class="sxs-lookup"><span data-stu-id="57c74-105">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="57c74-106">Ensuite, elle peut accepter un jeton d’IIS représentant un utilisateur disposant de droits inférieurs, effectuer une opération et revenir à nouveau à l’identité précédente.</span><span class="sxs-lookup"><span data-stu-id="57c74-106">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="57c74-107">Dans les situations où votre application doit emprunter l’identité d’un compte Windows qui n’a pas été attaché au thread actuel par IIS, vous devez extraire le jeton du compte et l’utiliser pour activer le compte.</span><span class="sxs-lookup"><span data-stu-id="57c74-107">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="57c74-108">Pour cela, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="57c74-108">You can do this by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="57c74-109">Récupérez le jeton de compte pour un utilisateur particulier en appelant la méthode **LogonUser** non managée.</span><span class="sxs-lookup"><span data-stu-id="57c74-109">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="57c74-110">Cette méthode ne figure pas dans la bibliothèque de classes de base du .NET Framework, mais dans le fichier **advapi32.dll** non managé.</span><span class="sxs-lookup"><span data-stu-id="57c74-110">This method is not in the .NET Framework base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="57c74-111">L’accès aux méthodes dans du code non managé est une opération complexe qui dépasse le cadre de cette discussion.</span><span class="sxs-lookup"><span data-stu-id="57c74-111">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="57c74-112">Pour plus d’informations, consultez [Interopération avec du code non managé](../../framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="57c74-112">For more information, see [Interoperating with Unmanaged Code](../../framework/interop/index.md).</span></span> <span data-ttu-id="57c74-113">Pour plus d’informations sur la méthode **LogonUser** et **advapi32.dll**, consultez la documentation du SDK de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="57c74-113">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2. <span data-ttu-id="57c74-114">Créez une nouvelle instance de la classe **WindowsIdentity**, qui passe le jeton.</span><span class="sxs-lookup"><span data-stu-id="57c74-114">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="57c74-115">Le code suivant illustre cet appel, où `hToken` désigne un jeton Windows.</span><span class="sxs-lookup"><span data-stu-id="57c74-115">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. <span data-ttu-id="57c74-116">Commencez l’emprunt d’identité en créant une instance de la classe <xref:System.Security.Principal.WindowsImpersonationContext> et en l’initialisant avec la méthode <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> de la classe initialisée, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="57c74-116">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. <span data-ttu-id="57c74-117">Quand vous n’avez plus besoin d’emprunter l’identité, appelez la méthode <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> pour rétablir l’emprunt d’identité, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="57c74-117">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="57c74-118">Si du code approuvé a déjà attaché un <xref:System.Security.Principal.WindowsPrincipal> objet au thread, vous pouvez appeler la méthode d’instance **Impersonate**, qui ne prend pas de jeton de compte.</span><span class="sxs-lookup"><span data-stu-id="57c74-118">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="57c74-119">Notez que cela est utile uniquement lorsque l’objet **WindowsPrincipal** sur le thread représente un utilisateur autre que celui sous lequel le processus est exécuté.</span><span class="sxs-lookup"><span data-stu-id="57c74-119">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="57c74-120">Par exemple, vous pouvez rencontrer cette situation quand vous utilisez ASP.NET avec l’authentification Windows activée et l’emprunt d’identité désactivé.</span><span class="sxs-lookup"><span data-stu-id="57c74-120">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="57c74-121">Dans ce cas, le processus s’exécute sous un compte configuré dans Internet Information Services (IIS), tandis que le principal actuel représente l’utilisateur Windows qui accède à la page.</span><span class="sxs-lookup"><span data-stu-id="57c74-121">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="57c74-122">Notez que ni **Impersonate** ni **Undo** ne modifie l’objet **principal** ( <xref:System.Security.Principal.IPrincipal> ) associé au contexte d’appel actuel.</span><span class="sxs-lookup"><span data-stu-id="57c74-122">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="57c74-123">Au lieu de cela, l’emprunt d’identité et le rétablissement modifient le jeton associé au processus de système d’exploitation actuel.</span><span class="sxs-lookup"><span data-stu-id="57c74-123">Rather, impersonation and reverting change the token associated with the current operating system process..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c74-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57c74-124">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [<span data-ttu-id="57c74-125">Objets Principal et Identity</span><span class="sxs-lookup"><span data-stu-id="57c74-125">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="57c74-126">Interopération avec du code non managé</span><span class="sxs-lookup"><span data-stu-id="57c74-126">Interoperating with Unmanaged Code</span></span>](../../framework/interop/index.md)
