---
title: Demandes de liaison
description: En savoir plus sur les demandes de liaison, ce qui entraîne une vérification de la sécurité pendant la compilation juste-à-temps (JIT) et l’examen de l’assembly appelant immédiat de votre code.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
ms.openlocfilehash: 7f5475d5bfff8cc3c500f95b05d54daacc9b253e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855788"
---
# <a name="link-demands"></a><span data-ttu-id="747d0-103">Demandes de liaison</span><span class="sxs-lookup"><span data-stu-id="747d0-103">Link Demands</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="747d0-104">Une demande de liaison entraîne une vérification de sécurité pendant la compilation juste-à-temps. Seul l'assembly appelant immédiat de votre code est vérifié.</span><span class="sxs-lookup"><span data-stu-id="747d0-104">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="747d0-105">La liaison est établie quand le code est lié à une référence de type, y compris les références de pointeur fonction et les appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="747d0-105">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="747d0-106">Si l'assembly appelant ne dispose pas des autorisations suffisantes pour établir une liaison avec votre code, la liaison n'est pas autorisée et une exception d'exécution est levée quand le code est chargé et exécuté.</span><span class="sxs-lookup"><span data-stu-id="747d0-106">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="747d0-107">Les demandes de liaison peuvent être substituées dans les classes qui héritent de votre code.</span><span class="sxs-lookup"><span data-stu-id="747d0-107">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="747d0-108">Un parcours de pile complet n’est pas effectué avec ce type de demande et que votre code est toujours vulnérable aux attaques par leurre.</span><span class="sxs-lookup"><span data-stu-id="747d0-108">A full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="747d0-109">Par exemple, si une méthode de l’assembly A est protégée par une demande de liaison, un appelant direct de l’assembly B est évalué en fonction des autorisations de l’assembly B.  Toutefois, la demande de liaison n’évaluera pas une méthode dans l’assembly C si elle appelle indirectement la méthode dans l’assembly A à l’aide de la méthode de l’assembly B. La demande de liaison spécifie uniquement les autorisations que les appelants directs dans l’assembly appelant immédiat doivent avoir pour créer un lien vers votre code.</span><span class="sxs-lookup"><span data-stu-id="747d0-109">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="747d0-110">Elle ne spécifie pas les autorisations que tous les appelants doivent avoir pour exécuter votre code.</span><span class="sxs-lookup"><span data-stu-id="747d0-110">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="747d0-111">Les modificateurs de parcours de pile <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A> et <xref:System.Security.CodeAccessPermission.PermitOnly%2A> n'affectent pas l'évaluation des demandes de liaison.</span><span class="sxs-lookup"><span data-stu-id="747d0-111">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="747d0-112">Étant donné que les demandes de liaison n'effectuent pas de parcours de pile, les modificateurs de parcours de pile n'ont aucun effet sur les demandes de liaison.</span><span class="sxs-lookup"><span data-stu-id="747d0-112">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="747d0-113">Si une méthode protégée par une demande de liaison est accessible par [réflexion](../reflection-and-codedom/reflection.md), une demande de liaison vérifie l’appelant immédiat du code accessible via la réflexion.</span><span class="sxs-lookup"><span data-stu-id="747d0-113">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="747d0-114">Cela est vrai à la fois pour les détections de méthodes et les appels de méthodes effectués à l'aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="747d0-114">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="747d0-115">Par exemple, supposons que le code utilise la réflexion pour retourner un <xref:System.Reflection.MethodInfo> objet représentant une méthode protégée par une demande de liaison, puis passe cet objet **MethodInfo** à un autre code qui utilise l’objet pour appeler la méthode d’origine.</span><span class="sxs-lookup"><span data-stu-id="747d0-115">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="747d0-116">Dans ce cas, la vérification de la demande de liaison se produit deux fois : une fois pour le code qui retourne l’objet **MethodInfo** et une fois pour le code qui l’appelle.</span><span class="sxs-lookup"><span data-stu-id="747d0-116">In this case, the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="747d0-117">Une demande de liaison exécutée sur un constructeur de classe statique ne protège pas le constructeur, car les constructeurs statiques sont appelés par le système, en dehors du chemin d’exécution du code de l’application.</span><span class="sxs-lookup"><span data-stu-id="747d0-117">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="747d0-118">Par conséquent, quand une demande de liaison est appliquée à une classe entière, elle ne peut pas protéger l'accès à un constructeur statique, même si elle protège le reste de la classe.</span><span class="sxs-lookup"><span data-stu-id="747d0-118">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="747d0-119">Le fragment de code suivant spécifie de manière déclarative que tout code lié à la méthode `ReadData` doit avoir l'autorisation `CustomPermission`.</span><span class="sxs-lookup"><span data-stu-id="747d0-119">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="747d0-120">Cette autorisation est une autorisation personnalisée hypothétique et n'existe pas dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="747d0-120">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="747d0-121">La demande est effectuée en passant un indicateur **SecurityAction. LinkDemand** à `CustomPermissionAttribute` .</span><span class="sxs-lookup"><span data-stu-id="747d0-121">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="747d0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="747d0-122">See also</span></span>

- [<span data-ttu-id="747d0-123">Attributs</span><span class="sxs-lookup"><span data-stu-id="747d0-123">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="747d0-124">Sécurité d’accès du code</span><span class="sxs-lookup"><span data-stu-id="747d0-124">Code Access Security</span></span>](code-access-security.md)
