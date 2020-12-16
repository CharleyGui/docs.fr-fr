---
title: Erreur SYSLIB0002
description: En savoir plus sur le obsoletion qui génère des erreurs de compilation SYSLIB0002.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 774675e96d11a8e1b5d82767695d0defd1e8cfad
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596506"
---
# <a name="syslib0002-principalpermissionattribute-is-obsolete"></a><span data-ttu-id="3cbac-103">SYSLIB0002 : PrincipalPermissionAttribute est obsolète</span><span class="sxs-lookup"><span data-stu-id="3cbac-103">SYSLIB0002: PrincipalPermissionAttribute is obsolete</span></span>

<span data-ttu-id="3cbac-104">Le <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructeur est obsolète et génère des erreurs au moment `SYSLIB0002` de la compilation, à compter de .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="3cbac-104">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces compile-time error `SYSLIB0002`, starting in .NET 5.0.</span></span> <span data-ttu-id="3cbac-105">Vous ne pouvez pas instancier cet attribut ou l’appliquer à une méthode.</span><span class="sxs-lookup"><span data-stu-id="3cbac-105">You cannot instantiate this attribute or apply it to a method.</span></span>

<span data-ttu-id="3cbac-106">Contrairement à d’autres avertissements obsoletion, vous ne pouvez pas supprimer l’erreur.</span><span class="sxs-lookup"><span data-stu-id="3cbac-106">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="3cbac-107">Solutions de contournement</span><span class="sxs-lookup"><span data-stu-id="3cbac-107">Workarounds</span></span>

- <span data-ttu-id="3cbac-108">Si vous appliquez l’attribut à une méthode d’action MVC ASP.NET :</span><span class="sxs-lookup"><span data-stu-id="3cbac-108">If you're applying the attribute to an ASP.NET MVC action method:</span></span>

  <span data-ttu-id="3cbac-109">Envisagez d’utiliser ASP. Infrastructure d’autorisation intégrée à .net.</span><span class="sxs-lookup"><span data-stu-id="3cbac-109">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="3cbac-110">Le code suivant montre comment annoter un contrôleur avec un <xref:System.Web.Mvc.AuthorizeAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="3cbac-110">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="3cbac-111">Le runtime ASP.NET autorise l’utilisateur avant d’effectuer l’action.</span><span class="sxs-lookup"><span data-stu-id="3cbac-111">The ASP.NET runtime will authorize the user before performing the action.</span></span>

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

  <span data-ttu-id="3cbac-112">Pour plus d’informations, consultez [autorisation basée sur les rôles dans ASP.net Core](/aspnet/core/security/authorization/roles) et [Présentation de l’autorisation dans ASP.net Core](/aspnet/core/security/authorization/introduction).</span><span class="sxs-lookup"><span data-stu-id="3cbac-112">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="3cbac-113">Si vous appliquez l’attribut au code de bibliothèque en dehors du contexte d’une application Web :</span><span class="sxs-lookup"><span data-stu-id="3cbac-113">If you're applying the attribute to library code outside the context of a web app:</span></span>

  <span data-ttu-id="3cbac-114">Effectuez les vérifications manuellement au début de votre méthode en appelant la <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="3cbac-114">Perform the checks manually at the beginning of your method by calling the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

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

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="3cbac-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cbac-115">See also</span></span>

- [<span data-ttu-id="3cbac-116">PrincipalPermissionAttribute est obsolète en tant qu’erreur</span><span class="sxs-lookup"><span data-stu-id="3cbac-116">PrincipalPermissionAttribute is obsolete as error</span></span>](../core-libraries/5.0/principalpermissionattribute-obsolete.md)
