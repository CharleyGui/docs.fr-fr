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
ms.openlocfilehash: 92e49af78d42f360d5798a72d4e7b981295947e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181101"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="d42f3-102">Utilisation de la méthode Assert</span><span class="sxs-lookup"><span data-stu-id="d42f3-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="d42f3-103"><xref:System.Security.CodeAccessPermission.Assert%2A> est une méthode qui peut être appelée sur les classes d'autorisation d'accès au code et sur la classe <xref:System.Security.PermissionSet>.</span><span class="sxs-lookup"><span data-stu-id="d42f3-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="d42f3-104">Vous pouvez utiliser **Assert** pour activer votre code (et les appelants en aval) pour effectuer des actions que votre code a la permission de faire, mais ses appelants pourraient ne pas avoir la permission de faire.</span><span class="sxs-lookup"><span data-stu-id="d42f3-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="d42f3-105">Une assertion de sécurité modifie le processus normal de vérification de sécurité effectué par le runtime.</span><span class="sxs-lookup"><span data-stu-id="d42f3-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="d42f3-106">Lors de l'assertion d'une autorisation, le système de sécurité reçoit l'ordre de ne pas vérifier que les appelants de votre code disposent de l'autorisation ayant fait l'objet d'une assertion.</span><span class="sxs-lookup"><span data-stu-id="d42f3-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="d42f3-107">Utilisez les assertions avec précaution, car elles peuvent ouvrir des failles de sécurité et perturber le mécanisme d'application des restrictions de sécurité du runtime.</span><span class="sxs-lookup"><span data-stu-id="d42f3-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="d42f3-108">Les assertions sont utiles quand une bibliothèque appelle du code non managé ou effectue un appel qui nécessite une autorisation qui n'est pas liée de manière évidente à l'utilisation prévue de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="d42f3-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="d42f3-109">Par exemple, tout le code géré qui appelle dans le code non géré doit avoir **SecurityPermission** avec le drapeau **UnmanagedCode** spécifié.</span><span class="sxs-lookup"><span data-stu-id="d42f3-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="d42f3-110">Par défaut, le code qui ne provient pas de l'ordinateur local, comme le code téléchargé à partir de l'intranet local, ne recevra pas cette autorisation.</span><span class="sxs-lookup"><span data-stu-id="d42f3-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="d42f3-111">Par conséquent, pour que le code téléchargé à partir de l'intranet local puisse appeler une bibliothèque qui utilise du code non managé, il doit disposer de l'autorisation ayant fait l'objet d'une assertion effectuée par la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="d42f3-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="d42f3-112">En outre, certaines bibliothèques peuvent effectuer des appels invisibles aux appelants et nécessitent donc des autorisations spéciales.</span><span class="sxs-lookup"><span data-stu-id="d42f3-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="d42f3-113">Vous pouvez également utiliser des assertions quand votre code accède à une ressource d'une manière totalement invisible pour les appelants.</span><span class="sxs-lookup"><span data-stu-id="d42f3-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="d42f3-114">Supposons, par exemple, que votre bibliothèque obtienne des informations d'une base de données, mais que, pendant le processus, elle lise également les informations du Registre de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d42f3-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="d42f3-115">Étant donné que les développeurs qui utilisent votre bibliothèque n’ont pas accès à votre source, ils n’ont aucun moyen de savoir que leur code exige **RegistryPermission** pour utiliser votre code.</span><span class="sxs-lookup"><span data-stu-id="d42f3-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="d42f3-116">Dans ce cas, si vous décidez qu'il n'est pas raisonnable ni nécessaire d'exiger que les appelants de votre code aient l'autorisation d'accéder au Registre, vous pouvez procéder à l'assertion de l'autorisation pour la lecture du Registre.</span><span class="sxs-lookup"><span data-stu-id="d42f3-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="d42f3-117">Dans ce cas, il est approprié que la bibliothèque affirme la permission afin que les appelants sans **RegistrePermission** puissent utiliser la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="d42f3-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="d42f3-118">L'assertion n'affecte le parcours de pile que si l'autorisation ayant fait l'objet de l'assertion et une autorisation demandée par un appelant en aval sont de même type, et si l'autorisation demandée est un sous-ensemble de l'autorisation ayant fait l'objet de l'assertion.</span><span class="sxs-lookup"><span data-stu-id="d42f3-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="d42f3-119">Par exemple, si vous affirmez **FileIOPermission** pour lire tous les fichiers sur le lecteur C, et une demande en aval est faite pour **FileIOPermission** pour lire les fichiers dans C:Temp, l’affirmation pourrait affecter la marche de pile; toutefois, si la demande était que **FileIOPermission** écrive à la commande C, l’affirmation n’aurait aucun effet.</span><span class="sxs-lookup"><span data-stu-id="d42f3-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="d42f3-120">Pour effectuer des assertions, votre code doit disposer de l'autorisation faisant l'objet de l'assertion et de <xref:System.Security.Permissions.SecurityPermission>, qui représente le droit d'effectuer des assertions.</span><span class="sxs-lookup"><span data-stu-id="d42f3-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="d42f3-121">Il est possible d'effectuer une assertion pour une autorisation qui n'a pas été octroyée à votre code. Toutefois, une telle assertion serait inutile puisque la vérification de sécurité échouerait avant même que l'assertion n'ait pu faire en sorte qu'elle réussisse.</span><span class="sxs-lookup"><span data-stu-id="d42f3-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="d42f3-122">L’illustration suivante montre ce qui se passe lorsque vous utilisez **Assert**.</span><span class="sxs-lookup"><span data-stu-id="d42f3-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="d42f3-123">Supposons que les instructions suivantes soient vraies concernant les assemblys A, B, C, E et F, et les deux autorisations P1 et P1A :</span><span class="sxs-lookup"><span data-stu-id="d42f3-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="d42f3-124">P1A représente le droit de lire les fichiers .txt présents sur le lecteur C.</span><span class="sxs-lookup"><span data-stu-id="d42f3-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="d42f3-125">P1 représente le droit de lire tous les fichiers présents sur le lecteur C.</span><span class="sxs-lookup"><span data-stu-id="d42f3-125">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="d42f3-126">P1A et P1 sont tous deux des types **fileIOPermission,** et P1A est un sous-ensemble de P1.</span><span class="sxs-lookup"><span data-stu-id="d42f3-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="d42f3-127">Les assemblys E et F ont reçu l'autorisation P1A.</span><span class="sxs-lookup"><span data-stu-id="d42f3-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="d42f3-128">L'assembly C a reçu l'autorisation P1.</span><span class="sxs-lookup"><span data-stu-id="d42f3-128">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="d42f3-129">Les assemblys A et B n'ont reçu ni l'autorisation P1 ni l'autorisation P1A.</span><span class="sxs-lookup"><span data-stu-id="d42f3-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="d42f3-130">La méthode A est contenue dans l'assembly A, la méthode B dans l'assembly B, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="d42f3-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Diagramme qui montre les assemblages de méthode Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 <span data-ttu-id="d42f3-132">Dans ce scénario, la méthode A appelle B, B appelle C, C appelle E, et E appelle F. Méthode C affirme la permission de lire les fichiers sur le lecteur C (permission P1), et la méthode E exige la permission de lire les fichiers .txt sur le lecteur C (permission P1A).</span><span class="sxs-lookup"><span data-stu-id="d42f3-132">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="d42f3-133">Lorsque la demande en F est rencontrée au moment de l’exécution, une promenade de pile est effectuée pour vérifier les autorisations de tous les appelants de F, à commencer par E. E a été accordé la permission P1A, de sorte que la promenade de pile procède à examiner les autorisations de C, où l’affirmation de C est découvert.</span><span class="sxs-lookup"><span data-stu-id="d42f3-133">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="d42f3-134">Étant donné que l'autorisation demandée (P1A) est un sous-ensemble de l'autorisation ayant fait l'objet de l'assertion (P1), le parcours de pile s'arrête et la vérification de sécurité réussit automatiquement.</span><span class="sxs-lookup"><span data-stu-id="d42f3-134">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="d42f3-135">Il n'est pas important que les assemblys A et B ne disposent pas de l'autorisation P1A.</span><span class="sxs-lookup"><span data-stu-id="d42f3-135">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="d42f3-136">En procédant à l'assertion de P1, la méthode C garantit que ses appelants puissent accéder à la ressource protégée par P1, même s'ils n'ont pas reçu l'autorisation d'y accéder.</span><span class="sxs-lookup"><span data-stu-id="d42f3-136">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="d42f3-137">Si vous concevez une bibliothèque de classes et si une classe accède à une ressource protégée, vous devez, dans la plupart des cas, effectuer une demande de sécurité exigeant que les appelants de la classe possèdent l'autorisation appropriée.</span><span class="sxs-lookup"><span data-stu-id="d42f3-137">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="d42f3-138">Si la classe effectue alors une opération pour laquelle vous savez que la plupart de ses appelants n’auront pas la permission, et si vous êtes prêt à prendre la responsabilité de laisser ces appelants appeler votre code, vous pouvez affirmer la permission en appelant la méthode **Assert** sur un objet d’autorisation qui représente l’opération que le code effectue.</span><span class="sxs-lookup"><span data-stu-id="d42f3-138">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="d42f3-139">L’utilisation **d’Assert** de cette façon permet aux appelants qui normalement ne pouvaient pas le faire appeler votre code.</span><span class="sxs-lookup"><span data-stu-id="d42f3-139">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="d42f3-140">Par conséquent, si vous procédez à l'assertion d'une autorisation, soyez sûr d'effectuer au préalable les vérifications de sécurité appropriées pour empêcher une utilisation abusive de votre composant.</span><span class="sxs-lookup"><span data-stu-id="d42f3-140">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="d42f3-141">Supposons, par exemple, que votre classe de bibliothèque hautement approuvée possède une méthode qui supprime les fichiers.</span><span class="sxs-lookup"><span data-stu-id="d42f3-141">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="d42f3-142">Elle accède au fichier en appelant une fonction Win32 non managée.</span><span class="sxs-lookup"><span data-stu-id="d42f3-142">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="d42f3-143">Un appelant invoque la méthode **Supprimer** de votre code, en passant au nom du fichier à supprimer, C: 'Test.txt.</span><span class="sxs-lookup"><span data-stu-id="d42f3-143">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="d42f3-144">Dans la méthode **Supprimer,** <xref:System.Security.Permissions.FileIOPermission> votre code crée un objet représentant l’accès à C: 'Test.txt.</span><span class="sxs-lookup"><span data-stu-id="d42f3-144">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="d42f3-145">(L’accès à la rédaction est nécessaire pour supprimer un fichier.) Votre code invoque ensuite un contrôle de sécurité impérative en appelant la méthode **de demande** de l’objet **FileIOPermission.**</span><span class="sxs-lookup"><span data-stu-id="d42f3-145">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="d42f3-146">Si l'un des appelants de la pile des appels n'a pas cette autorisation, une <xref:System.Security.SecurityException> est levée.</span><span class="sxs-lookup"><span data-stu-id="d42f3-146">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="d42f3-147">Si aucune exception n'est levée, vous savez que tous les appelants ont le droit d'accéder à C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="d42f3-147">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="d42f3-148">Parce que vous croyez que la plupart de vos appelants n’auront pas <xref:System.Security.Permissions.SecurityPermission> la permission d’accéder au code non menté, votre code crée alors un objet qui représente le droit d’appeler du code non menté et appelle la méthode **Assert** de l’objet.</span><span class="sxs-lookup"><span data-stu-id="d42f3-148">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="d42f3-149">Enfin, il appelle la fonction non managée Win32 pour supprimer C:\Text.txt, puis retourne le contrôle à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="d42f3-149">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="d42f3-150">Vous devez être sûr que votre code n'utilise pas d'assertions s'il peut être utilisé par un autre code pour accéder à une ressource protégée par l'autorisation faisant l'objet de l'assertion.</span><span class="sxs-lookup"><span data-stu-id="d42f3-150">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="d42f3-151">Par exemple, dans le code qui écrit à un fichier dont le nom est spécifié par l’appelant comme paramètre, vous n’affirmeriez pas le **FileIOPermission** pour écrire à des fichiers parce que votre code serait ouvert à une utilisation abusive par un tiers.</span><span class="sxs-lookup"><span data-stu-id="d42f3-151">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="d42f3-152">Lorsque vous utilisez la syntaxe de sécurité impérative, appeler la méthode **Assert** sur plusieurs autorisations dans la même méthode provoque une exception de sécurité à jeter.</span><span class="sxs-lookup"><span data-stu-id="d42f3-152">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="d42f3-153">Au lieu de cela, vous devez créer un objet **PermissionSet,** lui passer les autorisations individuelles que vous souhaitez invoquer, puis appeler la méthode **Assert** sur **l’objet PermissionSet.**</span><span class="sxs-lookup"><span data-stu-id="d42f3-153">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="d42f3-154">Vous pouvez appeler la méthode **Assert** plus d’une fois lorsque vous utilisez la syntaxe de sécurité déclarative.</span><span class="sxs-lookup"><span data-stu-id="d42f3-154">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="d42f3-155">L’exemple suivant montre la syntaxe déclarative pour les contrôles de sécurité prépondérants à l’aide de la méthode **Assert.**</span><span class="sxs-lookup"><span data-stu-id="d42f3-155">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="d42f3-156">Notez que la syntaxe **FileIOPermissionAttribute** tient deux valeurs : un <xref:System.Security.Permissions.SecurityAction> recensement et l’emplacement du fichier ou de l’annuaire auquel l’autorisation doit être accordée.</span><span class="sxs-lookup"><span data-stu-id="d42f3-156">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="d42f3-157">L’appel à **Assert** provoque `C:\Log.txt` des demandes d’accès à la réussite, même si les appelants ne sont pas vérifiés pour la permission d’accéder au fichier.</span><span class="sxs-lookup"><span data-stu-id="d42f3-157">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="d42f3-158">Les fragments de code suivants montrent une syntaxe impérative pour les contrôles de sécurité prépondéraux à l’aide de la méthode **Assert.**</span><span class="sxs-lookup"><span data-stu-id="d42f3-158">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="d42f3-159">Dans cet exemple, un cas de l’objet **FileIOPermission** est déclaré.</span><span class="sxs-lookup"><span data-stu-id="d42f3-159">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="d42f3-160">Son constructeur est adopté **FileIOPermissionAccess.AllAccess** pour définir le type d’accès autorisé, suivi d’une chaîne décrivant l’emplacement du fichier.</span><span class="sxs-lookup"><span data-stu-id="d42f3-160">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="d42f3-161">Une fois **l’objet FileIOPermission** défini, vous n’avez qu’à appeler sa méthode **Assert** pour passer outre au contrôle de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d42f3-161">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d42f3-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d42f3-162">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="d42f3-163">Attributs</span><span class="sxs-lookup"><span data-stu-id="d42f3-163">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="d42f3-164">Sécurité d’accès au code</span><span class="sxs-lookup"><span data-stu-id="d42f3-164">Code Access Security</span></span>](code-access-security.md)
