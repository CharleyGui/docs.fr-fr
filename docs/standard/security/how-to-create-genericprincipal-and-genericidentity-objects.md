---
title: 'Procédure : créer des objets GenericPrincipal et GenericIdentity'
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
ms.openlocfilehash: cde4669a1bac49d1d9fde39c99707561379aec19
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818991"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="ebfce-102">Procédure : créer des objets GenericPrincipal et GenericIdentity</span><span class="sxs-lookup"><span data-stu-id="ebfce-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>

> [!NOTE]
> <span data-ttu-id="ebfce-103">Cet article s’applique à Windows.</span><span class="sxs-lookup"><span data-stu-id="ebfce-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="ebfce-104">Pour plus d’informations sur la ASP.NET Core, consultez [vue d’ensemble de la sécurité ASP.net Core](/aspnet/core/security/).</span><span class="sxs-lookup"><span data-stu-id="ebfce-104">For information about ASP.NET Core, see [Overview of ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="ebfce-105">Vous pouvez utiliser la <xref:System.Security.Principal.GenericIdentity> classe conjointement avec la <xref:System.Security.Principal.GenericPrincipal> classe pour créer un schéma d’autorisation qui existe indépendamment d’un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="ebfce-105">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>

### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="ebfce-106">Pour créer un objet GenericPrincipal</span><span class="sxs-lookup"><span data-stu-id="ebfce-106">To create a GenericPrincipal object</span></span>

1. <span data-ttu-id="ebfce-107">Créez une instance de la classe identity et initialisez-la avec le nom que vous souhaitez conserver.</span><span class="sxs-lookup"><span data-stu-id="ebfce-107">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="ebfce-108">Le code suivant crée un objet **GenericIdentity** et l’initialise avec le nom `MyUser`.</span><span class="sxs-lookup"><span data-stu-id="ebfce-108">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. <span data-ttu-id="ebfce-109">Créez une instance de la classe **GenericPrincipal** et initialisez-la avec l’objet **GenericIdentity** créé précédemment et un tableau de chaînes qui représentent les rôles que vous souhaitez associer à ce principal.</span><span class="sxs-lookup"><span data-stu-id="ebfce-109">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="ebfce-110">L’exemple de code suivant spécifie un tableau de chaînes qui représentent un rôle d’administrateur et un rôle d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ebfce-110">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="ebfce-111">Le **GenericPrincipal** est ensuite initialisé avec le **GenericIdentity** précédent et le tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="ebfce-111">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. <span data-ttu-id="ebfce-112">Utilisez le code suivant pour joindre le principal au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="ebfce-112">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="ebfce-113">Cela est utile dans les situations où le principal doit être validé plusieurs fois, qu’il doit être validé par un autre code s’exécutant dans votre application ou qu’il doit être validé par un <xref:System.Security.Permissions.PrincipalPermission> objet.</span><span class="sxs-lookup"><span data-stu-id="ebfce-113">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="ebfce-114">Vous pouvez toujours exécuter une validation basée sur les rôles sur l’objet principal sans le joindre au thread.</span><span class="sxs-lookup"><span data-stu-id="ebfce-114">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="ebfce-115">Pour plus d’informations, consultez [Remplacement d’un objet Principal](replacing-a-principal-object.md).</span><span class="sxs-lookup"><span data-stu-id="ebfce-115">For more information, see [Replacing a Principal Object](replacing-a-principal-object.md).</span></span>

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a><span data-ttu-id="ebfce-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="ebfce-116">Example</span></span>

<span data-ttu-id="ebfce-117">L’exemple de code suivant montre comment créer une instance d’un **GenericPrincipal** et d’un **GenericIdentity**.</span><span class="sxs-lookup"><span data-stu-id="ebfce-117">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="ebfce-118">Ce code affiche les valeurs de ces objets dans la console.</span><span class="sxs-lookup"><span data-stu-id="ebfce-118">This code displays the values of these objects to the console.</span></span>

```vb
Imports System.Security.Principal
Imports System.Threading

Public Class Class1

    Public Shared Sub Main()
        ' Create generic identity.
        Dim myIdentity As New GenericIdentity("MyIdentity")

        ' Create generic principal.
        Dim myStringArray As String() =  {"Manager", "Teller"}
        Dim myPrincipal As New GenericPrincipal(myIdentity, myStringArray)

        ' Attach the principal to the current thread.
        ' This is not required unless repeated validation must occur,
        ' other code in your application must validate, or the
        ' PrincipalPermission object is used.
        Thread.CurrentPrincipal = myPrincipal

        ' Print values to the console.
        Dim name As String = myPrincipal.Identity.Name
        Dim auth As Boolean = myPrincipal.Identity.IsAuthenticated
        Dim isInRole As Boolean = myPrincipal.IsInRole("Manager")

        Console.WriteLine("The name is: {0}", name)
        Console.WriteLine("The isAuthenticated is: {0}", auth)
        Console.WriteLine("Is this a Manager? {0}", isInRole)

    End Sub

End Class
```

```csharp
using System;
using System.Security.Principal;
using System.Threading;

public class Class1
{
    public static int Main(string[] args)
    {
    // Create generic identity.
    GenericIdentity myIdentity = new GenericIdentity("MyIdentity");

    // Create generic principal.
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal =
        new GenericPrincipal(myIdentity, myStringArray);

    // Attach the principal to the current thread.
    // This is not required unless repeated validation must occur,
    // other code in your application must validate, or the
    // PrincipalPermission object is used.
    Thread.CurrentPrincipal = myPrincipal;

    // Print values to the console.
    String name =  myPrincipal.Identity.Name;
    bool auth =  myPrincipal.Identity.IsAuthenticated;
    bool isInRole =  myPrincipal.IsInRole("Manager");

    Console.WriteLine("The name is: {0}", name);
    Console.WriteLine("The isAuthenticated is: {0}", auth);
    Console.WriteLine("Is this a Manager? {0}", isInRole);

    return 0;
    }
}
```

<span data-ttu-id="ebfce-119">Lorsqu’elle est exécutée, l’application affiche une sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="ebfce-119">When executed, the application displays output similar to the following.</span></span>

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a><span data-ttu-id="ebfce-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebfce-120">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="ebfce-121">Remplacement d'un objet Principal</span><span class="sxs-lookup"><span data-stu-id="ebfce-121">Replacing a Principal Object</span></span>](replacing-a-principal-object.md)
- [<span data-ttu-id="ebfce-122">Objets Principal et Identity</span><span class="sxs-lookup"><span data-stu-id="ebfce-122">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
