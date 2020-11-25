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
# <a name="principalpermissionattribute-is-obsolete-as-error"></a>PrincipalPermissionAttribute est obsolète en tant qu’erreur

Le <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructeur est obsolète et génère une erreur au moment de la compilation. Vous ne pouvez pas instancier cet attribut ou l’appliquer à une méthode.

## <a name="change-description"></a>Description de la modification

Sur .NET Framework et .NET Core, vous pouvez annoter des méthodes avec l' <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribut. Par exemple :

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

À compter de .NET 5,0, vous ne pouvez pas appliquer l' <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribut à une méthode. Le constructeur de l’attribut est obsolète et génère une erreur au moment de la compilation. Contrairement à d’autres avertissements obsoletion, vous ne pouvez pas supprimer l’erreur.

## <a name="reason-for-change"></a>Motif de modification

Le <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, comme les autres types dont la sous-classe <xref:System.Security.Permissions.SecurityAttribute> fait partie. Infrastructure de sécurité d’accès du code (CAS) du réseau. Dans .NET Framework 2. x-4. x, le runtime applique les <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations sur l’entrée de la méthode, même si l’application s’exécute dans un scénario de confiance totale. .NET Core et .NET 5,0 et versions ultérieures ne prennent pas en charge les attributs CAS, et le runtime les ignore.

Cette différence de comportement entre .NET Framework et .net Core et .NET 5,0 peut entraîner un scénario « d’échec d’ouverture », où l’accès aurait dû être bloqué mais a été autorisé à la place. Pour éviter le scénario « d’échec d’ouverture », vous ne pouvez plus appliquer l’attribut dans le code qui cible .NET 5,0 ou une version ultérieure.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name=""></a><a id="permission-action">Action recommandée</a>

Si vous rencontrez l’erreur obsoletion, vous devez prendre des mesures.

- **Si vous appliquez l’attribut à une méthode d’action MVC ASP.NET :**

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

- **Si vous appliquez l’attribut au code de bibliothèque en dehors du contexte d’une application Web :**

  Effectuez les vérifications manuellement au début de votre méthode. Cette opération peut être effectuée à l’aide de la <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> méthode.

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

## <a name="affected-apis"></a>API affectées

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
