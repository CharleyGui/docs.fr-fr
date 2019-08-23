---
title: Utilisation de la méthode Assert
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b5a13b362f565cfae9247908bcf3cf35c899ae4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910716"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="d3d18-102">Utilisation de la méthode Assert</span><span class="sxs-lookup"><span data-stu-id="d3d18-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="d3d18-103"><xref:System.Security.CodeAccessPermission.Assert%2A> est une méthode qui peut être appelée sur les classes d'autorisation d'accès au code et sur la classe <xref:System.Security.PermissionSet>.</span><span class="sxs-lookup"><span data-stu-id="d3d18-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="d3d18-104">Vous pouvez utiliser **Assert** pour permettre à votre code (et aux appelants en aval) d’effectuer des actions que votre code est autorisé à effectuer, mais que ses appelants ne sont pas autorisés à effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="d3d18-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="d3d18-105">Une assertion de sécurité modifie le processus normal de vérification de sécurité effectué par le runtime.</span><span class="sxs-lookup"><span data-stu-id="d3d18-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="d3d18-106">Lors de l'assertion d'une autorisation, le système de sécurité reçoit l'ordre de ne pas vérifier que les appelants de votre code disposent de l'autorisation ayant fait l'objet d'une assertion.</span><span class="sxs-lookup"><span data-stu-id="d3d18-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d3d18-107">Utilisez les assertions avec précaution, car elles peuvent ouvrir des failles de sécurité et perturber le mécanisme d'application des restrictions de sécurité du runtime.</span><span class="sxs-lookup"><span data-stu-id="d3d18-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="d3d18-108">Les assertions sont utiles quand une bibliothèque appelle du code non managé ou effectue un appel qui nécessite une autorisation qui n'est pas liée de manière évidente à l'utilisation prévue de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="d3d18-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="d3d18-109">Par exemple, tout le code managé qui appelle du code non managé doit avoir **SecurityPermission** avec l’indicateur **UnmanagedCode** spécifié.</span><span class="sxs-lookup"><span data-stu-id="d3d18-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="d3d18-110">Par défaut, le code qui ne provient pas de l'ordinateur local, comme le code téléchargé à partir de l'intranet local, ne recevra pas cette autorisation.</span><span class="sxs-lookup"><span data-stu-id="d3d18-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="d3d18-111">Par conséquent, pour que le code téléchargé à partir de l'intranet local puisse appeler une bibliothèque qui utilise du code non managé, il doit disposer de l'autorisation ayant fait l'objet d'une assertion effectuée par la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="d3d18-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="d3d18-112">En outre, certaines bibliothèques peuvent effectuer des appels invisibles aux appelants et nécessitent donc des autorisations spéciales.</span><span class="sxs-lookup"><span data-stu-id="d3d18-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="d3d18-113">Vous pouvez également utiliser des assertions quand votre code accède à une ressource d'une manière totalement invisible pour les appelants.</span><span class="sxs-lookup"><span data-stu-id="d3d18-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="d3d18-114">Supposons, par exemple, que votre bibliothèque obtienne des informations d'une base de données, mais que, pendant le processus, elle lise également les informations du Registre de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d3d18-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="d3d18-115">Étant donné que les développeurs qui utilisent votre bibliothèque n’ont pas accès à votre source, ils n’ont aucun moyen de savoir que leur code requiert **RegistryPermission** pour pouvoir utiliser votre code.</span><span class="sxs-lookup"><span data-stu-id="d3d18-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="d3d18-116">Dans ce cas, si vous décidez qu'il n'est pas raisonnable ni nécessaire d'exiger que les appelants de votre code aient l'autorisation d'accéder au Registre, vous pouvez procéder à l'assertion de l'autorisation pour la lecture du Registre.</span><span class="sxs-lookup"><span data-stu-id="d3d18-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="d3d18-117">Dans ce cas, il convient que la bibliothèque déclare l’autorisation afin que les appelants sans **RegistryPermission** puissent utiliser la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="d3d18-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="d3d18-118">L'assertion n'affecte le parcours de pile que si l'autorisation ayant fait l'objet de l'assertion et une autorisation demandée par un appelant en aval sont de même type, et si l'autorisation demandée est un sous-ensemble de l'autorisation ayant fait l'objet de l'assertion.</span><span class="sxs-lookup"><span data-stu-id="d3d18-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="d3d18-119">Par exemple, si vous déclarez **FileIOPermission** pour lire tous les fichiers sur le lecteur C, et qu’une demande en aval est effectuée pour que **FileIOPermission** lise les fichiers dans C:\temp, l’assertion peut affecter le parcours de la pile. Toutefois, si la demande était pour **FileIOPermission** d’écrire sur le lecteur C, l’assertion n’aurait aucun effet.</span><span class="sxs-lookup"><span data-stu-id="d3d18-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="d3d18-120">Pour effectuer des assertions, votre code doit disposer de l'autorisation faisant l'objet de l'assertion et de <xref:System.Security.Permissions.SecurityPermission>, qui représente le droit d'effectuer des assertions.</span><span class="sxs-lookup"><span data-stu-id="d3d18-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="d3d18-121">Il est possible d'effectuer une assertion pour une autorisation qui n'a pas été octroyée à votre code. Toutefois, une telle assertion serait inutile puisque la vérification de sécurité échouerait avant même que l'assertion n'ait pu faire en sorte qu'elle réussisse.</span><span class="sxs-lookup"><span data-stu-id="d3d18-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="d3d18-122">L’illustration suivante montre ce qui se passe lorsquevous utilisez Assert.</span><span class="sxs-lookup"><span data-stu-id="d3d18-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="d3d18-123">Supposons que les instructions suivantes soient vraies concernant les assemblys A, B, C, E et F, et les deux autorisations P1 et P1A :</span><span class="sxs-lookup"><span data-stu-id="d3d18-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="d3d18-124">P1A représente le droit de lire les fichiers .txt présents sur le lecteur C.</span><span class="sxs-lookup"><span data-stu-id="d3d18-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="d3d18-125">P1 représente le droit de lire tous les fichiers présents sur le lecteur C.</span><span class="sxs-lookup"><span data-stu-id="d3d18-125">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="d3d18-126">P1A et P1 sont tous deux des types **FileIOPermission** et P1A est un sous-ensemble de P1.</span><span class="sxs-lookup"><span data-stu-id="d3d18-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="d3d18-127">Les assemblys E et F ont reçu l'autorisation P1A.</span><span class="sxs-lookup"><span data-stu-id="d3d18-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="d3d18-128">L'assembly C a reçu l'autorisation P1.</span><span class="sxs-lookup"><span data-stu-id="d3d18-128">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="d3d18-129">Les assemblys A et B n'ont reçu ni l'autorisation P1 ni l'autorisation P1A.</span><span class="sxs-lookup"><span data-stu-id="d3d18-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="d3d18-130">La méthode A est contenue dans l'assembly A, la méthode B dans l'assembly B, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="d3d18-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Diagramme qui affiche les assemblys de la méthode Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)    
  
 <span data-ttu-id="d3d18-132">Dans ce scénario, la méthode A appelle B, B appelle C, C appelle E, et E appelle F. la méthode C déclare l’autorisation de lire des fichiers sur le lecteur C (autorisation P1), et la méthode E demande l’autorisation de lire les fichiers. txt sur le lecteur C (autorisation P1A).</span><span class="sxs-lookup"><span data-stu-id="d3d18-132">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="d3d18-133">Quand la demande en F est rencontrée au moment de l’exécution, un parcours de pile est effectué pour vérifier les autorisations de tous les appelants de F, en commençant par E. E a reçu l’autorisation P1A, le parcours de pile continue donc à examiner les autorisations de C, où l’assertion de C est découverte.</span><span class="sxs-lookup"><span data-stu-id="d3d18-133">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="d3d18-134">Étant donné que l'autorisation demandée (P1A) est un sous-ensemble de l'autorisation ayant fait l'objet de l'assertion (P1), le parcours de pile s'arrête et la vérification de sécurité réussit automatiquement.</span><span class="sxs-lookup"><span data-stu-id="d3d18-134">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="d3d18-135">Il n'est pas important que les assemblys A et B ne disposent pas de l'autorisation P1A.</span><span class="sxs-lookup"><span data-stu-id="d3d18-135">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="d3d18-136">En procédant à l'assertion de P1, la méthode C garantit que ses appelants puissent accéder à la ressource protégée par P1, même s'ils n'ont pas reçu l'autorisation d'y accéder.</span><span class="sxs-lookup"><span data-stu-id="d3d18-136">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="d3d18-137">Si vous concevez une bibliothèque de classes et si une classe accède à une ressource protégée, vous devez, dans la plupart des cas, effectuer une demande de sécurité exigeant que les appelants de la classe possèdent l'autorisation appropriée.</span><span class="sxs-lookup"><span data-stu-id="d3d18-137">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="d3d18-138">Si la classe effectue ensuite une opération pour laquelle vous savez que la plupart de ses appelants n’auront pas d’autorisation, et si vous êtes disposé à prendre la responsabilité de laisser ces appelants appeler votre code, vous pouvez déclarer l’autorisation en appelant la méthode Assert sur un objet d’autorisation qui représente l’opération exécutée par le code.</span><span class="sxs-lookup"><span data-stu-id="d3d18-138">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="d3d18-139">L' utilisation de la méthode Assert permet aux appelants qui n’ont pas normalement pu le faire d’appeler votre code.</span><span class="sxs-lookup"><span data-stu-id="d3d18-139">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="d3d18-140">Par conséquent, si vous procédez à l'assertion d'une autorisation, soyez sûr d'effectuer au préalable les vérifications de sécurité appropriées pour empêcher une utilisation abusive de votre composant.</span><span class="sxs-lookup"><span data-stu-id="d3d18-140">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="d3d18-141">Supposons, par exemple, que votre classe de bibliothèque hautement approuvée possède une méthode qui supprime les fichiers.</span><span class="sxs-lookup"><span data-stu-id="d3d18-141">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="d3d18-142">Elle accède au fichier en appelant une fonction Win32 non managée.</span><span class="sxs-lookup"><span data-stu-id="d3d18-142">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="d3d18-143">Un appelant appelle la méthode **Delete** de votre code, en passant le nom du fichier à supprimer, C:\test.txt.</span><span class="sxs-lookup"><span data-stu-id="d3d18-143">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="d3d18-144">Dans la méthode **Delete** , votre code crée un <xref:System.Security.Permissions.FileIOPermission> objet représentant l’accès en écriture à C:\test.txt.</span><span class="sxs-lookup"><span data-stu-id="d3d18-144">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="d3d18-145">(l'accès en écriture est nécessaire pour supprimer un fichier). Votre code appelle ensuite une vérification de sécurité impérative en appelant la méthode **Demand** de l’objet **FileIOPermission** .</span><span class="sxs-lookup"><span data-stu-id="d3d18-145">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="d3d18-146">Si l'un des appelants de la pile des appels n'a pas cette autorisation, une <xref:System.Security.SecurityException> est levée.</span><span class="sxs-lookup"><span data-stu-id="d3d18-146">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="d3d18-147">Si aucune exception n'est levée, vous savez que tous les appelants ont le droit d'accéder à C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="d3d18-147">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="d3d18-148">Comme vous pensez que la plupart de vos appelants ne sont pas autorisés à accéder à du code non managé, votre code crée <xref:System.Security.Permissions.SecurityPermission> ensuite un objet qui représente le droit d’appeler du code non managé et appelle la méthode Assert de l’objet.</span><span class="sxs-lookup"><span data-stu-id="d3d18-148">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="d3d18-149">Enfin, il appelle la fonction non managée Win32 pour supprimer C:\Text.txt, puis retourne le contrôle à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="d3d18-149">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d3d18-150">Vous devez être sûr que votre code n'utilise pas d'assertions s'il peut être utilisé par un autre code pour accéder à une ressource protégée par l'autorisation faisant l'objet de l'assertion.</span><span class="sxs-lookup"><span data-stu-id="d3d18-150">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="d3d18-151">Par exemple, dans le code qui écrit dans un fichier dont le nom est spécifié par l’appelant en tant que paramètre, vous ne devez pas déclarer l' **autorisation FileIOPermission** pour écrire dans les fichiers, car votre code est ouvert à une utilisation incorrecte par un tiers.</span><span class="sxs-lookup"><span data-stu-id="d3d18-151">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="d3d18-152">Lorsque vous utilisez la syntaxe de sécurité impérative, l' appel de la méthode Assert sur plusieurs autorisations dans la même méthode entraîne la levée d’une exception de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d3d18-152">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="d3d18-153">Au lieu de cela, vous devez créer un objet PermissionSet, lui passer les autorisations individuelles que vous souhaitez appeler, puis appeler la méthode Assert sur l’objet PermissionSet.</span><span class="sxs-lookup"><span data-stu-id="d3d18-153">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="d3d18-154">Vous pouvez appeler la méthode Assert plusieurs fois lorsque vous utilisez la syntaxe de sécurité déclarative.</span><span class="sxs-lookup"><span data-stu-id="d3d18-154">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="d3d18-155">L’exemple suivant illustre la syntaxe déclarative pour la substitution des vérifications de sécurité à l’aide de la méthode Assert.</span><span class="sxs-lookup"><span data-stu-id="d3d18-155">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="d3d18-156">Notez que la syntaxe **FileIOPermissionAttribute** accepte deux valeurs: une <xref:System.Security.Permissions.SecurityAction> Énumération et l’emplacement du fichier ou du répertoire auquel l’autorisation doit être accordée.</span><span class="sxs-lookup"><span data-stu-id="d3d18-156">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="d3d18-157">L’appel à **Assert** entraîne la réussie des `C:\Log.txt` demandes d’accès à, même si l’autorisation d’accès au fichier n’est pas activée pour les appelants.</span><span class="sxs-lookup"><span data-stu-id="d3d18-157">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub   
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {     
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}   
```  
  
 <span data-ttu-id="d3d18-158">Les fragments de code suivants illustrent la syntaxe impérative pour la substitution des vérifications de sécurité à l’aide de la méthode Assert.</span><span class="sxs-lookup"><span data-stu-id="d3d18-158">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="d3d18-159">Dans cet exemple, une instance de l’objet **FileIOPermission** est déclarée.</span><span class="sxs-lookup"><span data-stu-id="d3d18-159">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="d3d18-160">Le constructeur reçoit **FileIOPermissionAccess. AllAccess** pour définir le type d’accès autorisé, suivi d’une chaîne décrivant l’emplacement du fichier.</span><span class="sxs-lookup"><span data-stu-id="d3d18-160">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="d3d18-161">Une fois l’objet **FileIOPermission** défini, il vous suffit d’appeler sa méthode Assert pour remplacer la vérification de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d3d18-161">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");   
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3d18-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3d18-162">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="d3d18-163">Attributs</span><span class="sxs-lookup"><span data-stu-id="d3d18-163">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="d3d18-164">Sécurité d’accès du code</span><span class="sxs-lookup"><span data-stu-id="d3d18-164">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
