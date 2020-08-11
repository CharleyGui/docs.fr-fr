---
title: Gestion de l’état
description: Découvrez les différentes approches de la gestion de l’État dans ASP.NET Web Forms et éblouissant.
author: csharpfritz
ms.author: jefritz
ms.date: 05/15/2020
ms.openlocfilehash: bac2f00330113725f09259ca31bdf857a8769f24
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062338"
---
# <a name="state-management"></a>Gestion de l’état

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

La gestion d’État est un concept clé des applications Web Forms, facilitant l’état d’affichage, l’état de session, l’état de l’application et les fonctionnalités de publication (postback). Ces fonctionnalités avec état de l’infrastructure ont permis de masquer la gestion des États requise pour une application et permettent aux développeurs d’applications de se concentrer sur la prestation de leurs fonctionnalités. Avec ASP.NET Core et éblouissant, certaines de ces fonctionnalités ont été déplacées et d’autres ont été supprimées entièrement. Ce chapitre passe en revue la façon de maintenir l’État et de fournir les mêmes fonctionnalités avec les nouvelles fonctionnalités de éblouissant.

## <a name="request-state-management-with-viewstate"></a>Demander la gestion de l’état avec ViewState

Lorsque vous aborderez la gestion des États dans Web Forms application, de nombreux développeurs pensent immédiatement à ViewState. Dans Web Forms, ViewState gère l’état du contenu entre les requêtes HTTP en envoyant un grand bloc de texte encodé dans le navigateur. Le champ ViewState peut être submergé par le contenu d’une page contenant de nombreux éléments, ce qui peut s’étendre à plusieurs mégaoctets.

Avec le serveur éblouissant, l’application maintient une connexion continue avec le serveur. L’état de l’application, appelé *circuit*, est conservé dans la mémoire du serveur pendant que la connexion est considérée comme active. L’État est supprimé uniquement lorsque l’utilisateur quitte l’application ou une page particulière de l’application. Tous les membres des composants actifs sont disponibles entre les interactions avec le serveur.

Cette fonctionnalité présente plusieurs avantages :

- L’état du composant est immédiatement disponible et n’est pas régénéré entre les interactions.
- L’État n’est pas transmis au navigateur.

Toutefois, il existe quelques inconvénients à la persistance de l’état des composants en mémoire à connaître :

- Si le serveur redémarre entre les demandes, l’État est perdu.
- La solution d’équilibrage de charge de votre serveur Web d’application doit inclure des sessions rémanentes pour s’assurer que toutes les demandes du même navigateur reviennent au même serveur. Si une demande est envoyée à un autre serveur, l’État sera perdu.
- La persistance de l’état des composants sur le serveur peut entraîner une sollicitation de la mémoire sur le serveur Web.

Pour les raisons précédentes, ne vous fiez pas uniquement à l’état du composant pour qu’il se trouve en mémoire sur le serveur. Votre application doit également inclure un magasin de données de stockage pour les données entre les demandes. Voici quelques exemples simples de cette stratégie :

- Dans une application de panier d’achat, conserver le contenu des nouveaux éléments ajoutés au panier dans un enregistrement de base de données. Si l’État sur le serveur est perdu, vous pouvez le reconstituer à partir des enregistrements de la base de données.
- Dans un formulaire Web en plusieurs parties, vos utilisateurs s’attendent à ce que votre application mémorise les valeurs entre chaque requête. Écrivez les données entre chacune des publications de votre utilisateur dans un magasin de données afin qu’elles puissent être extraites et assemblées dans la structure de réponse finale du formulaire lorsque le formulaire en plusieurs parties est terminé.

Pour plus d’informations sur la gestion de l’État dans les applications éblouissantes, consultez ASP.NET Core la gestion de l' [État éblouissant](/aspnet/core/blazor/state-management).

## <a name="maintain-state-with-session"></a>Conserver l’état avec la session

Web Forms les développeurs peuvent conserver des informations sur l’utilisateur en cours d’utilisation avec l' <xref:Microsoft.AspNetCore.Http.ISession?displayProperty=nameWithType> objet Dictionary. Il est assez simple d’ajouter un objet avec une clé de chaîne à la `Session` , et cet objet sera disponible ultérieurement pendant les interactions de l’utilisateur avec l’application. Pour tenter d’éliminer la gestion de l’interaction avec HTTP, l’objet a facilité la `Session` conservation de l’État.

La signature de l' `Session` objet .NET Framework n’est pas la même que l' `Session` objet ASP.net core. Examinez [la documentation relative à la nouvelle session de ASP.net Core](/dotnet/api/microsoft.aspnetcore.http.isession) avant de décider de migrer et d’utiliser la nouvelle fonctionnalité d’état de session.

La session est disponible dans ASP.NET Core et le serveur éblouissant, mais il est déconseillé de l’utiliser en faveur du stockage des données dans un référentiel de données de manière appropriée. L’état de session ne fonctionne pas non plus si les visiteurs refusent l’utilisation de cookies HTTP dans votre application en raison de problèmes de confidentialité.

La configuration de ASP.NET Core et de l’état de session est disponible dans l' [article gestion de session et d’État dans ASP.net Core](/aspnet/core/fundamentals/app-state#session-state).

## <a name="application-state"></a>État de l’application

L' `Application` objet dans le Web Forms Framework fournit un référentiel de requête massive pour interagir avec l’État et la configuration de l’étendue de l’application. L’état de l’application était idéal pour stocker diverses propriétés de configuration de l’application qui seraient référencées par toutes les demandes, quel que soit l’utilisateur qui a effectué la demande. Le problème avec l' `Application` objet était que les données n’étaient pas conservées sur plusieurs serveurs. L’état de l’objet d’application a été perdu entre les redémarrages.

Comme avec `Session` , il est recommandé de déplacer les données vers un magasin de stockage persistant accessible par plusieurs instances de serveur. S’il existe des données volatiles auxquelles vous souhaitez pouvoir accéder entre les demandes et les utilisateurs, vous pouvez facilement les stocker dans un service singleton qui peut être injecté dans des composants qui requièrent ces informations ou cette interaction.

La construction d’un objet pour conserver l’état de l’application et sa consommation peuvent ressembler à l’implémentation suivante :

```csharp
public class MyApplicationState
{
    public int VisitorCounter { get; private set; } = 0;

    public void IncrementCounter() => VisitorCounter += 1;
}
```

```csharp
app.AddSingleton<MyApplicationState>();
```

```razor
@inject MyApplicationState AppState

<label>Total Visitors: @AppState.VisitorCounter</label>
```

L' `MyApplicationState` objet n’est créé qu’une seule fois sur le serveur, et la valeur `VisitorCounter` est extraite et sortie dans l’étiquette du composant. La `VisitorCounter` valeur doit être conservée et récupérée à partir d’un magasin de données de sauvegarde pour des fins de durabilité et d’évolutivité.

## <a name="in-the-browser"></a>Dans le navigateur

Les données d’application peuvent également être stockées côté client sur l’appareil de l’utilisateur afin d’être disponibles ultérieurement. Il existe deux fonctionnalités de navigateur qui permettent la persistance des données dans différentes étendues du navigateur de l’utilisateur :

- `localStorage`-étendue au navigateur entier de l’utilisateur. Si la page est rechargée, le navigateur est fermé, rouvert, ou un autre onglet est ouvert avec la même URL, alors le même `localStorage` est fourni par le navigateur.
- `sessionStorage`-étendue à l’onglet de navigateur actuel de l’utilisateur. Si l’onglet est rechargé, l’état persiste. Toutefois, si l’utilisateur ouvre un autre onglet pour votre application ou ferme et ouvre à nouveau le navigateur, l’État est perdu.

Vous pouvez écrire du code JavaScript personnalisé pour interagir avec ces fonctionnalités, ou il existe un certain nombre de packages NuGet que vous pouvez utiliser pour fournir cette fonctionnalité. L’un de ces packages est [Microsoft. AspNetCore. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.ProtectedBrowserStorage).

Pour obtenir des instructions sur l’utilisation de ce package pour interagir avec `localStorage` et `sessionStorage` , consultez l’article sur la gestion de l' [État éblouissant](/aspnet/core/blazor/state-management#protected-browser-storage-experimental-package) .

>[!div class="step-by-step"]
>[Précédent](pages-routing-layouts.md) 
> [Suivant](forms-validation.md)
