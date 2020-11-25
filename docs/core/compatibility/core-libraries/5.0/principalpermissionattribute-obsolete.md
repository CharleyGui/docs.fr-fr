---
title: 'Modification avec rupture : PrincipalPermissionAttribute est obsolète en tant qu’erreur'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où le constructeur PrincipalPermissionAttribute est obsolète et génère une erreur de compilation.
ms.date: 11/01/2020
ms.openlocfilehash: 138bbf25fd493c1bb9c2b3f10b62681c735ea7b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760992"
---
# <a name="principalpermissionattribute-is-obsolete-as-error"></a><span data-ttu-id="b1f20-103">PrincipalPermissionAttribute est obsolète en tant qu’erreur</span><span class="sxs-lookup"><span data-stu-id="b1f20-103">PrincipalPermissionAttribute is obsolete as error</span></span>

<span data-ttu-id="b1f20-104">Le <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructeur est obsolète et génère une erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="b1f20-104">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="b1f20-105">Vous ne pouvez pas instancier cet attribut ou l’appliquer à une méthode.</span><span class="sxs-lookup"><span data-stu-id="b1f20-105">You cannot instantiate this attribute or apply it to a method.</span></span>

## <a name="change-description"></a><span data-ttu-id="b1f20-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="b1f20-106">Change description</span></span>

<span data-ttu-id="b1f20-107">Sur .NET Framework et .NET Core, vous pouvez annoter des méthodes avec l' <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="b1f20-107">On .NET Framework and .NET Core, you can annotate methods with the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute.</span></span> <span data-ttu-id="b1f20-108">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b1f20-108">For example:</span></span>

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

<span data-ttu-id="b1f20-109">À compter de .NET 5,0, vous ne pouvez pas appliquer l' <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribut à une méthode.</span><span class="sxs-lookup"><span data-stu-id="b1f20-109">Starting in .NET 5.0, you cannot apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a method.</span></span> <span data-ttu-id="b1f20-110">Le constructeur de l’attribut est obsolète et génère une erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="b1f20-110">The constructor for the attribute is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="b1f20-111">Contrairement à d’autres avertissements obsoletion, vous ne pouvez pas supprimer l’erreur.</span><span class="sxs-lookup"><span data-stu-id="b1f20-111">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b1f20-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="b1f20-112">Reason for change</span></span>

<span data-ttu-id="b1f20-113">Le <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, comme les autres types dont la sous-classe <xref:System.Security.Permissions.SecurityAttribute> fait partie. Infrastructure de sécurité d’accès du code (CAS) du réseau.</span><span class="sxs-lookup"><span data-stu-id="b1f20-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, like other types that subclass <xref:System.Security.Permissions.SecurityAttribute>, is part of .NET's Code Access Security (CAS) infrastructure.</span></span> <span data-ttu-id="b1f20-114">Dans .NET Framework 2. x-4. x, le runtime applique les <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations sur l’entrée de la méthode, même si l’application s’exécute dans un scénario de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="b1f20-114">In .NET Framework 2.x - 4.x, the runtime enforces <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations on method entry, even if the application is running under a full-trust scenario.</span></span> <span data-ttu-id="b1f20-115">.NET Core et .NET 5,0 et versions ultérieures ne prennent pas en charge les attributs CAS, et le runtime les ignore.</span><span class="sxs-lookup"><span data-stu-id="b1f20-115">.NET Core and .NET 5.0 and later don't support CAS attributes, and the runtime ignores them.</span></span>

<span data-ttu-id="b1f20-116">Cette différence de comportement entre .NET Framework et .net Core et .NET 5,0 peut entraîner un scénario « d’échec d’ouverture », où l’accès aurait dû être bloqué mais a été autorisé à la place.</span><span class="sxs-lookup"><span data-stu-id="b1f20-116">This difference in behavior from .NET Framework to .NET Core and .NET 5.0 can result in a "fail open" scenario, where access should have been blocked but instead has been allowed.</span></span> <span data-ttu-id="b1f20-117">Pour éviter le scénario « d’échec d’ouverture », vous ne pouvez plus appliquer l’attribut dans le code qui cible .NET 5,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="b1f20-117">To prevent the "fail open" scenario, you can no longer apply the attribute in code that targets .NET 5.0 or later.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b1f20-118">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b1f20-118">Version introduced</span></span>

<span data-ttu-id="b1f20-119">5.0</span><span class="sxs-lookup"><span data-stu-id="b1f20-119">5.0</span></span>

## <a name=""></a><span data-ttu-id="b1f20-120"><a id="permission-action">Action recommandée</a></span><span class="sxs-lookup"><span data-stu-id="b1f20-120"><a id="permission-action">Recommended action</a></span></span>

<span data-ttu-id="b1f20-121">Si vous rencontrez l’erreur obsoletion, vous devez prendre des mesures.</span><span class="sxs-lookup"><span data-stu-id="b1f20-121">If you encounter the obsoletion error, you must take action.</span></span>

- <span data-ttu-id="b1f20-122">**Si vous appliquez l’attribut à une méthode d’action MVC ASP.NET :**</span><span class="sxs-lookup"><span data-stu-id="b1f20-122">**If you're applying the attribute to an ASP.NET MVC action method:**</span></span>

  <span data-ttu-id="b1f20-123">Envisagez d’utiliser ASP. Infrastructure d’autorisation intégrée à .net.</span><span class="sxs-lookup"><span data-stu-id="b1f20-123">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="b1f20-124">Le code suivant montre comment annoter un contrôleur avec un <xref:System.Web.Mvc.AuthorizeAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="b1f20-124">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="b1f20-125">Le runtime ASP.NET autorise l’utilisateur avant d’effectuer l’action.</span><span class="sxs-lookup"><span data-stu-id="b1f20-125">The ASP.NET runtime will authorize the user before performing the action.</span></span>

  ```csharp
  using Microsoft.AspNetCore.Authorization;

  namespace MySampleApp
  {
      [Authorize(Roles = "Administrator")]
      public class AdministrationController : Controller
      {
          public ActionResult MyAction()
          {
              // This code won't run unless the current user
              // is in the 'Administrator' role.
          }
      }
  }
  ```

  <span data-ttu-id="b1f20-126">Pour plus d’informations, consultez [autorisation basée sur les rôles dans ASP.net Core](/aspnet/core/security/authorization/roles) et [Présentation de l’autorisation dans ASP.net Core](/aspnet/core/security/authorization/introduction).</span><span class="sxs-lookup"><span data-stu-id="b1f20-126">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="b1f20-127">**Si vous appliquez l’attribut au code de bibliothèque en dehors du contexte d’une application Web :**</span><span class="sxs-lookup"><span data-stu-id="b1f20-127">**If you're applying the attribute to library code outside the context of a web app:**</span></span>

  <span data-ttu-id="b1f20-128">Effectuez les vérifications manuellement au début de votre méthode.</span><span class="sxs-lookup"><span data-stu-id="b1f20-128">Perform the checks manually at the beginning of your method.</span></span> <span data-ttu-id="b1f20-129">Cette opération peut être effectuée à l’aide de la <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="b1f20-129">This can be done by using the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

  ```csharp
  using System.Threading;

  void DoSomething()
  {
      if (Thread.CurrentPrincipal == null
          || !Thread.CurrentPrincipal.IsInRole("Administrators"))
      {
          throw new Exception("User is anonymous or isn't an admin.");
      }

      // Code that should run only when user is an administrator.
  }
  ```

## <a name="affected-apis"></a><span data-ttu-id="b1f20-130">API affectées</span><span class="sxs-lookup"><span data-stu-id="b1f20-130">Affected APIs</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
