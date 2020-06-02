---
title: 'Comment : créer un objet WindowsPrincipal'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: 6064c98c4e1e5153f4e0de4849de196228972a89
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284427"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="b7d75-102">Comment : créer un objet WindowsPrincipal</span><span class="sxs-lookup"><span data-stu-id="b7d75-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="b7d75-103">Il existe deux façons de créer un objet <xref:System.Security.Principal.WindowsPrincipal>, selon que le code doit effectuer une ou plusieurs validations basées sur les rôles.</span><span class="sxs-lookup"><span data-stu-id="b7d75-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="b7d75-104">Si le code doit exécuter plusieurs validations basées sur les rôles, la première des procédures suivantes produira moins de surcharge.</span><span class="sxs-lookup"><span data-stu-id="b7d75-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="b7d75-105">Si le code ne doit exécuter qu’une seule validation basée sur les rôles, vous pouvez créer un objet <xref:System.Security.Principal.WindowsPrincipal> à l’aide de la deuxième procédure ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b7d75-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="b7d75-106">Pour créer un objet WindowsPrincipal pour une validation répétée</span><span class="sxs-lookup"><span data-stu-id="b7d75-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="b7d75-107">Appelez la méthode <xref:System.AppDomain.SetPrincipalPolicy%2A> sur l'objet <xref:System.AppDomain> qui est retourné par la propriété statique <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType>, en passant à la méthode une valeur d'énumération <xref:System.Security.Principal.PrincipalPolicy> qui indique la nouvelle stratégie.</span><span class="sxs-lookup"><span data-stu-id="b7d75-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="b7d75-108">Les valeurs prises en charge sont <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> et <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="b7d75-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="b7d75-109">Le code suivant illustre cet appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="b7d75-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="b7d75-110">Une fois la stratégie définie, utilisez la propriété statique <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> pour récupérer le principal qui encapsule l'utilisateur Windows actuel.</span><span class="sxs-lookup"><span data-stu-id="b7d75-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="b7d75-111">Étant donné que le type de retour de la propriété est <xref:System.Security.Principal.IPrincipal>, vous devez caster le résultat vers un type <xref:System.Security.Principal.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="b7d75-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="b7d75-112">Le code suivant initialise un nouvel objet <xref:System.Security.Principal.WindowsPrincipal> vers la valeur du principal associé au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="b7d75-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. <span data-ttu-id="b7d75-113">Quand l'objet principal a été créé, vous pouvez utiliser plusieurs méthodes pour le valider.</span><span class="sxs-lookup"><span data-stu-id="b7d75-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="b7d75-114">Pour créer un objet WindowsPrincipal pour une validation unique</span><span class="sxs-lookup"><span data-stu-id="b7d75-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="b7d75-115">Initialisez un nouvel objet <xref:System.Security.Principal.WindowsIdentity> en appelant la méthode statique <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType>, qui interroge le compte Windows actuel et place des informations sur ce compte dans l'objet d'identité récemment créé.</span><span class="sxs-lookup"><span data-stu-id="b7d75-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="b7d75-116">Le code suivant crée un nouvel objet <xref:System.Security.Principal.WindowsIdentity> et l'initialise vers l'utilisateur authentifié actuel.</span><span class="sxs-lookup"><span data-stu-id="b7d75-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="b7d75-117">Créez un objet <xref:System.Security.Principal.WindowsPrincipal> et passez-lui la valeur de l'objet <xref:System.Security.Principal.WindowsIdentity> créé à l'étape précédente.</span><span class="sxs-lookup"><span data-stu-id="b7d75-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="b7d75-118">Quand l'objet principal a été créé, vous pouvez utiliser plusieurs méthodes pour le valider.</span><span class="sxs-lookup"><span data-stu-id="b7d75-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d75-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7d75-119">See also</span></span>

- [<span data-ttu-id="b7d75-120">Objets Principal et Identity</span><span class="sxs-lookup"><span data-stu-id="b7d75-120">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
