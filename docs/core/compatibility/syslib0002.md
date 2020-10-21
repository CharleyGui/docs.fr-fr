---
title: Erreur SYSLIB0002
description: En savoir plus sur le obsoletion qui génère des erreurs de compilation SYSLIB0002.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 00fd42975c9286221b75c87caef8d2109b9b7100
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333298"
---
# <a name="syslib0002-principalpermissionattribute-is-obsolete"></a>SYSLIB0002 : PrincipalPermissionAttribute est obsolète

Le <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructeur est obsolète et génère des erreurs au moment `SYSLIB0002` de la compilation, à compter de .net 5,0. Vous ne pouvez pas instancier cet attribut ou l’appliquer à une méthode.

Contrairement à d’autres avertissements obsoletion, vous ne pouvez pas supprimer l’erreur.

## <a name="workarounds"></a>Solutions de contournement

- Si vous appliquez l’attribut à une méthode d’action MVC ASP.NET :

  Envisagez d’utiliser ASP. Infrastructure d’autorisation intégrée à .net. Le code suivant montre comment annoter un contrôleur avec un <xref:System.Web.Mvc.AuthorizeAttribute> attribut. Le runtime ASP.NET autorise l’utilisateur avant d’effectuer l’action.

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

  Pour plus d’informations, consultez [autorisation basée sur les rôles dans ASP.net Core](/aspnet/core/security/authorization/roles) et [Présentation de l’autorisation dans ASP.net Core](/aspnet/core/security/authorization/introduction).

- Si vous appliquez l’attribut au code de bibliothèque en dehors du contexte d’une application Web :

  Effectuez les vérifications manuellement au début de votre méthode en appelant la <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> méthode.

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

## <a name="see-also"></a>Voir aussi

- [PrincipalPermissionAttribute est obsolète en tant qu’erreur](3.1-5.0.md#principalpermissionattribute-is-obsolete-as-error)
