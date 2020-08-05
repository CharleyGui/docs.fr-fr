---
ms.openlocfilehash: 2c8a5c1ec87918a91600a3557c679a42cae74896
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556327"
---
### <a name="principalpermissionattribute-is-obsolete-as-error"></a><span data-ttu-id="60d61-101">PrincipalPermissionAttribute est obsolète en tant qu’erreur</span><span class="sxs-lookup"><span data-stu-id="60d61-101">PrincipalPermissionAttribute is obsolete as error</span></span>

<span data-ttu-id="60d61-102">Le <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructeur est obsolète et génère une erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="60d61-102">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="60d61-103">Vous ne pouvez pas instancier cet attribut ou l’appliquer à une méthode.</span><span class="sxs-lookup"><span data-stu-id="60d61-103">You cannot instantiate this attribute or apply it to a method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="60d61-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="60d61-104">Change description</span></span>

<span data-ttu-id="60d61-105">Sur .NET Framework et .NET Core, vous pouvez annoter des méthodes avec l' <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="60d61-105">On .NET Framework and .NET Core, you can annotate methods with the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute.</span></span> <span data-ttu-id="60d61-106">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="60d61-106">For example:</span></span>

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

<span data-ttu-id="60d61-107">À compter de .NET 5,0, vous ne pouvez pas appliquer l' <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribut à une méthode.</span><span class="sxs-lookup"><span data-stu-id="60d61-107">Starting in .NET 5.0, you cannot apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a method.</span></span> <span data-ttu-id="60d61-108">Le constructeur de l’attribut est obsolète et génère une erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="60d61-108">The constructor for the attribute is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="60d61-109">Contrairement à d’autres avertissements obsoletion, vous ne pouvez pas supprimer l’erreur.</span><span class="sxs-lookup"><span data-stu-id="60d61-109">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="60d61-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="60d61-110">Reason for change</span></span>

<span data-ttu-id="60d61-111">Le <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, comme les autres types dont la sous-classe <xref:System.Security.Permissions.SecurityAttribute> fait partie. Infrastructure de sécurité d’accès du code (CAS) du réseau.</span><span class="sxs-lookup"><span data-stu-id="60d61-111">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, like other types that subclass <xref:System.Security.Permissions.SecurityAttribute>, is part of .NET's Code Access Security (CAS) infrastructure.</span></span> <span data-ttu-id="60d61-112">Dans .NET Framework 2. x-4. x, le runtime applique les <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations sur l’entrée de la méthode, même si l’application s’exécute dans un scénario de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="60d61-112">In .NET Framework 2.x - 4.x, the runtime enforces <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations on method entry, even if the application is running under a full-trust scenario.</span></span> <span data-ttu-id="60d61-113">.NET Core et .NET 5,0 et versions ultérieures ne prennent pas en charge les attributs CAS, et le runtime les ignore.</span><span class="sxs-lookup"><span data-stu-id="60d61-113">.NET Core and .NET 5.0 and later don't support CAS attributes, and the runtime ignores them.</span></span>

<span data-ttu-id="60d61-114">Cette différence de comportement entre .NET Framework et .net Core et .NET 5,0 peut entraîner un scénario « d’échec d’ouverture », où l’accès aurait dû être bloqué mais a été autorisé à la place.</span><span class="sxs-lookup"><span data-stu-id="60d61-114">This difference in behavior from .NET Framework to .NET Core and .NET 5.0 can result in a "fail open" scenario, where access should have been blocked but instead has been allowed.</span></span> <span data-ttu-id="60d61-115">Pour éviter le scénario « d’échec d’ouverture », vous ne pouvez plus appliquer l’attribut dans le code qui cible .NET 5,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="60d61-115">To prevent the "fail open" scenario, you can no longer apply the attribute in code that targets .NET 5.0 or later.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="60d61-116">Version introduite</span><span class="sxs-lookup"><span data-stu-id="60d61-116">Version introduced</span></span>

<span data-ttu-id="60d61-117">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="60d61-117">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="60d61-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="60d61-118">Recommended action</span></span>

<span data-ttu-id="60d61-119">Si vous rencontrez l’erreur obsoletion, vous devez prendre des mesures.</span><span class="sxs-lookup"><span data-stu-id="60d61-119">If you encounter the obsoletion error, you must take action.</span></span>

- <span data-ttu-id="60d61-120">**Si vous appliquez l’attribut à une méthode d’action MVC ASP.NET :**</span><span class="sxs-lookup"><span data-stu-id="60d61-120">**If you're applying the attribute to an ASP.NET MVC action method:**</span></span>

  <span data-ttu-id="60d61-121">Envisagez d’utiliser ASP. Infrastructure d’autorisation intégrée à .net.</span><span class="sxs-lookup"><span data-stu-id="60d61-121">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="60d61-122">Le code suivant montre comment annoter un contrôleur avec un <xref:System.Web.Mvc.AuthorizeAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="60d61-122">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="60d61-123">Le runtime ASP.NET autorise l’utilisateur avant d’effectuer l’action.</span><span class="sxs-lookup"><span data-stu-id="60d61-123">The ASP.NET runtime will authorize the user before performing the action.</span></span>

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

  <span data-ttu-id="60d61-124">Pour plus d’informations, consultez [autorisation basée sur les rôles dans ASP.net Core](/aspnet/core/security/authorization/roles) et [Présentation de l’autorisation dans ASP.net Core](/aspnet/core/security/authorization/introduction).</span><span class="sxs-lookup"><span data-stu-id="60d61-124">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="60d61-125">**Si vous appliquez l’attribut au code de bibliothèque en dehors du contexte d’une application Web :**</span><span class="sxs-lookup"><span data-stu-id="60d61-125">**If you're applying the attribute to library code outside the context of a web app:**</span></span>

  <span data-ttu-id="60d61-126">Effectuez les vérifications manuellement au début de votre méthode.</span><span class="sxs-lookup"><span data-stu-id="60d61-126">Perform the checks manually at the beginning of your method.</span></span> <span data-ttu-id="60d61-127">Cette opération peut être effectuée à l’aide de la <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="60d61-127">This can be done by using the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

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

#### <a name="category"></a><span data-ttu-id="60d61-128">Category</span><span class="sxs-lookup"><span data-stu-id="60d61-128">Category</span></span>

- <span data-ttu-id="60d61-129">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="60d61-129">Core .NET libraries</span></span>
- <span data-ttu-id="60d61-130">Sécurité</span><span class="sxs-lookup"><span data-stu-id="60d61-130">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="60d61-131">API affectées</span><span class="sxs-lookup"><span data-stu-id="60d61-131">Affected APIs</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
