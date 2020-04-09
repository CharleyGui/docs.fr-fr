---
title: À propos de l’autorisation dans les microservices .NET et les applications web
description: Sécurité dans les microservices .NET et les applications web - Découvrez une vue d’ensemble des principales options d’autorisation dans les applications ASP.NET Core, basées sur le rôle et basées sur les stratégies.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 27936a33ea2bb46cedb9d10ee47a2117e1843e14
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988204"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>À propos de l’autorisation dans les microservices .NET et les applications web

Après l’authentification, les API web ASP.NET Core doivent autoriser l’accès. Ce processus permet à un service d’autoriser uniquement les utilisateurs authentifiés à accéder aux API. [L’autorisation](/aspnet/core/security/authorization/introduction) peut être faite en fonction des rôles des utilisateurs ou en fonction de la politique personnalisée, qui peut inclure l’inspection des réclamations ou d’autres heuristiques.

Restreindre l’accès à un ASP.NET’itinéraire Core MVC est aussi facile que l’application d’un attribut d’autorisation à la méthode d’action (ou à la catégorie du contrôleur si toutes les actions du contrôleur nécessitent une autorisation), comme le montre l’exemple suivant :

```csharp
public class AccountController : Controller
{
    public ActionResult Login()
    {
    }

    [Authorize]
    public ActionResult Logout()
    {
    }
}
```

Par défaut, l’ajout d’un attribut Authorize sans paramètres limite l’accès aux utilisateurs authentifiés pour le contrôleur ou l’action en question. Pour limiter un peu plus l’accès à un API à certains utilisateurs, l’attribut peut être étendu pour spécifier les rôles ou les stratégies que les utilisateurs doivent obligatoirement satisfaire.

## <a name="implement-role-based-authorization"></a>Implémenter une autorisation basée sur les rôles

L’identité ASP.NET Core intègre un concept de rôles. En plus des utilisateurs, l’identité ASP.NET Core stocke des informations sur les différents rôles utilisés par l’application et assure le suivi des utilisateurs et des rôles qui leur sont attribués. Ces attributions peuvent être modifiées par programmation avec le type `RoleManager` qui met à jour des rôles dans le stockage persistant, et le type `UserManager` qui peut accorder ou révoquer des rôles d’utilisateurs.

Si vous authentifiez avec des jetons de porteur JWT, le ASP.NET Core JWT bearer authentification middleware remplira les rôles d’un utilisateur en fonction des revendications de rôle trouvées dans le jeton. Pour limiter l’accès à une action ou à un contrôleur MVC aux seuls utilisateurs ayant un rôle déterminé, vous pouvez inclure un paramètre Roles dans l’annotation (attribut) Authorize, comme illustré dans le fragment de code suivant :

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
public class ControlPanelController : Controller
{
    public ActionResult SetTime()
    {
    }

    [Authorize(Roles = "Administrator")]
    public ActionResult ShutDown()
    {
    }
}
```

Dans cet exemple, seuls les utilisateurs appartenant aux rôles Administrator ou PowerUser peuvent accéder aux API dans le contrôleur ControlPanel (comme l’exécution de l’action SetTime). L’API ShutDown est soumise à des restrictions plus contraignantes puisque seuls les utilisateurs appartenant au rôle Administrator peuvent y accéder.

Pour exiger qu’un utilisateur appartienne à plusieurs rôles, vous devez utiliser plusieurs attributs Authorize, comme dans l’exemple suivant :

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

Dans cet exemple, pour appeler API1, un utilisateur doit :

- Appartenir au rôle Administrator *ou* PowerUser, *et*

- appartenir au rôle RemoteEmployee, *et*

- satisfaire un gestionnaire personnalisé pour l’autorisation CustomPolicy.

## <a name="implement-policy-based-authorization"></a>Implémenter une autorisation basée sur une stratégie

Des règles d’autorisation personnalisées peuvent aussi être écrites au moyen de [stratégies d’autorisation](https://docs.asp.net/en/latest/security/authorization/policies.html). Cette section fournit une vue d’ensemble. Pour plus d’informations, consultez l’[atelier sur l’autorisation ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Les stratégies d’autorisation personnalisées sont inscrites dans la méthode Startup.ConfigureServices via la méthode service.AddAuthorization. Cette méthode prend un délégué qui configure un argument AuthorizationOptions.

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("AdministratorsOnly", policy =>
        policy.RequireRole("Administrator"));

    options.AddPolicy("EmployeesOnly", policy =>
        policy.RequireClaim("EmployeeNumber"));

    options.AddPolicy("Over21", policy =>
        policy.Requirements.Add(new MinimumAgeRequirement(21)));
});
```

Comme le montre l’exemple, les stratégies peuvent être associées à différents types de conditions. Une fois les polices enregistrées, elles peuvent être appliquées à une action ou à un contrôleur `[Authorize(Policy="EmployeesOnly")]`en adoptant le nom de la police comme argument de la politique de l’attribut autorisation (par exemple, ) les politiques peuvent avoir de multiples exigences, et pas seulement une (comme le montrent ces exemples).

Dans l’exemple précédent, le premier appel AddPolicy est simplement une autre façon d’autoriser par rôle. Si `[Authorize(Policy="AdministratorsOnly")]` est appliqué à une API, seuls les utilisateurs ayant le rôle Administrator peuvent y accéder.

Le deuxième appel <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> présente une façon simple d’exiger la présence d’une revendication précise pour l’utilisateur. La méthode <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> peut aussi prendre les valeurs attendues de la revendication. Si des valeurs sont spécifiées, la condition n’est remplie que si l’utilisateur dispose d’une revendication du type approprié et de l’une des valeurs spécifiées. Si vous utilisez le middleware d’authentification du porteur JSON, toutes les propriétés JWT sont accessibles en tant que revendications d’utilisateur.

Parmi les stratégies présentées ici, la plus intéressante est celle qui se trouve dans la troisième méthode `AddPolicy`, car elle utilise une condition d’autorisation personnalisée. Le fait d’utiliser des conditions d’autorisation personnalisées vous permet de mieux contrôler la façon dont s’exerce l’autorisation. Pour que cela fonctionne, vous devez implémenter les types suivants :

- Un type Requirements qui dérive de <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> et qui contient des champs spécifiant les détails de la condition. Dans l’exemple, il s’agit d’un champ d’âge pour l’exemple de type `MinimumAgeRequirement`.

- Un gestionnaire qui implémente <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, où T est le type de <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> que le gestionnaire peut satisfaire. Le gestionnaire doit implémenter la méthode <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A>, qui vérifie si un contexte spécifié contenant des informations sur l’utilisateur remplit la condition.

Si l’utilisateur remplit la condition, un appel à `context.Succeed` indique que l’utilisateur est autorisé. Si un utilisateur peut satisfaire une condition d’autorisation de différentes manières, plusieurs gestionnaires peuvent être créés.

En plus de la nécessité d’inscrire des conditions de stratégie personnalisée avec des appels `AddPolicy`, vous devez aussi inscrire des gestionnaires de conditions personnalisés par le biais de l’injection de dépendance (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).

Un exemple d’exigence d’autorisation personnalisée et de gestionnaire `DateOfBirth` pour vérifier l’âge d’un utilisateur (basé sur une réclamation) est disponible dans la documentation d’autorisation de base ASP.NET . [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html)

## <a name="additional-resources"></a>Ressources supplémentaires

- **ASP.NET Authentification de base** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **autorisation de base ASP.NET** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- **Autorisation basée sur les rôles** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- **Autorisation personnalisée fondée sur les politiques** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Suivant précédent](index.md)
>[Next](developer-app-secrets-storage.md)
