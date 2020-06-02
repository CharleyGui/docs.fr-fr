---
title: Nouveautés de .NET Core 2.1
description: Découvrez les nouvelles fonctionnalités de .NET Core 2.1.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 3e6f3a921238a5897c7aa4b6034be979724b7167
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283440"
---
# <a name="whats-new-in-net-core-21"></a>Nouveautés de .NET Core 2.1

.NET Core 2.1 inclut les nouvelles fonctionnalités et améliorations dans les domaines suivants :

- [Outillage](#tooling)
- [Restaurer par progression](#roll-forward)
- [Déploiement](#deployment)
- [Pack de compatibilité Windows](#windows-compatibility-pack)
- [Améliorations de la compilation JIT](#jit-compiler-improvements)
- [Modifications d'API](#api-changes)

## <a name="tooling"></a>Outillage

Le Kit SDK.NET Core 2.1 (2.1.300), les outils inclus avec .NET Core 2.1, intègrent les modifications et améliorations suivantes :

### <a name="build-performance-improvements"></a>Amélioration des performances des builds

Un objectif majeur de .NET Core 2.1 est l’amélioration des performances des builds, en particulier pour les builds incrémentielles. Ces améliorations des performances s’appliquent aux builds en ligne de commande à l’aide de `dotnet build` et aux builds dans Visual Studio. Certaines zones individuelles d’amélioration incluent :

- Pour la résolution de ressources de package, résolution uniquement des ressources utilisées par une build plutôt que de toutes les ressources.

- Mise en cache des références d’assembly.

- Utilisation de serveurs de build SDK de longue durée, représentant des processus qui couvrent des appels `dotnet build` individuels. Ils suppriment la nécessité de la compilation JIT de grands blocs de code à chaque exécution de `dotnet build`. Les processus d’un serveur de build peuvent être automatiquement terminés avec la commande suivante :

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Nouvelles commandes CLI

Un certain nombre d’outils qui étaient disponibles uniquement par projet à l’aide de `DotnetCliToolReference` sont désormais disponibles dans le cadre du Kit de développement .NET Core. Ces outils incluent :

- `dotnet watch` fournit un observateur de système de fichiers qui attend la modification d’un fichier avant d’exécuter un ensemble désigné de commandes. Par exemple, la commande suivante reconstruit automatiquement le projet actuel et génère une sortie détaillée à chaque modification d’un fichier :

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   Remarquez l’option `--` qui précède l’option `--verbose`. Elle délimite les options passées directement à la commande `dotnet watch` à partir des arguments passés au processus enfant `dotnet`. Sans elle, l’option `--verbose` s’applique à la commande `dotnet watch`, et non à la commande `dotnet build`.
  
   Pour plus d’informations, consultez [développer des applications ASP.net core à l’aide de dotnet Watch](/aspnet/core/tutorials/dotnet-watch).

- `dotnet dev-certs` génère et gère les certificats utilisés pendant le développement dans les applications ASP.NET Core.

- `dotnet user-secrets` gère les secrets d’un magasin de secrets d’un utilisateur dans les applications ASP.NET Core.

- `dotnet sql-cache` crée un tableau et des index dans une base de données Microsoft SQL Server à utiliser pour la mise en cache distribuée.

- `dotnet ef` est un outil de gestion des bases de données, des objets <xref:Microsoft.EntityFrameworkCore.DbContext> et des migrations dans les applications Entity Framework Core. Pour plus d’informations, consultez [Outils en ligne de commande EF Core .NET](/ef/core/miscellaneous/cli/dotnet).

### <a name="global-tools"></a>Outils globaux

.NET Core 2.1 prend en charge les *outils globaux*, autrement dit des outils personnalisés disponibles globalement à partir de la ligne de commande. Le modèle d’extensibilité des versions précédentes de .NET Core proposant des outils personnalisés par projet uniquement à l’aide de `DotnetCliToolReference`.

Pour installer un outil global, vous utilisez la commande [dotnet tool install](../tools/dotnet-tool-install.md). Par exemple :

```dotnetcli
dotnet tool install -g dotnetsay
```

Une fois installé, l’outil peut être exécuté à partir de la ligne de commande en spécifiant le nom de l’outil. Pour plus d’informations, consultez [Vue d’ensemble des outils globaux .NET Core](../tools/global-tools.md).

### <a name="tool-management-with-the-dotnet-tool-command"></a>Gestion des outils avec la commande `dotnet tool`

Dans le SDK .NET Core 2.1, toutes les opérations avec les outils utilisent la commande `dotnet tool`. Les options suivantes sont disponibles :

- [`dotnet tool install`](../tools/dotnet-tool-install.md)pour installer un outil.

- [`dotnet tool update`](../tools/dotnet-tool-update.md)pour désinstaller et réinstaller un outil qui le met à jour.

- [`dotnet tool list`](../tools/dotnet-tool-list.md)pour répertorier les outils actuellement installés.

- [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md)pour désinstaller les outils actuellement installés.

## <a name="roll-forward"></a>Restauration par progression

Toutes les applications .NET Core depuis .NET Core 2.0 extrapolent automatiquement vers la dernière *version mineure* installée sur un système.

À compter de .NET Core 2,0, si la version de .NET Core avec laquelle une application a été générée n’est pas présente au moment de l’exécution, l’application s’exécute automatiquement sur la dernière *version mineure* installée de .net core. En d’autres termes, si une application est générée avec .NET Core 2.0 et que .NET Core 2.0 n’est pas présent sur le système hôte, mais que .NET Core 2.1 l’est, l’application s’exécute avec .NET Core 2.1.

> [!IMPORTANT]
> Ce comportement de restauration par progression ne s’applique pas aux préversions, Par défaut, il ne s’applique pas non plus aux versions majeures, mais vous pouvez changer ce comportement avec les paramètres ci-dessous.

Vous pouvez modifier ce comportement en changeant le paramètre d’extrapolation en cas d’absence de framework partagé candidat. Les paramètres disponibles sont :

- `0` : désactiver le comportement d’extrapolation de version mineure. Avec ce paramètre, une application conçue pour .NET Core 2.0.0 extrapole vers .NET Core 2.0.1, mais pas vers .NET Core 2.2.0 ou .NET Core 3.0.0.
- `1` : activer le comportement d’extrapolation de version mineure. Il s’agit de la valeur par défaut pour ce paramètre. Avec ce paramètre, une application conçue pour .NET Core 2.0.0 extrapole vers .NET Core 2.0.1 ou .NET Core 2.2.0 (en fonction de la version installée), mais n’extrapole pas vers .NET Core 3.0.0.
- `2` : activer le comportement d’extrapolation de version mineure et majeure. Si cette option est définie, même les versions majeures différentes sont prises en compte. Ainsi, une application conçue pour .NET Core 2.0.0 extrapole vers .NET Core 3.0.0.

Vous pouvez modifier ce paramètre de trois manières :

- Affectez à la variable d’environnement `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` la valeur souhaitée.

- Ajoutez la ligne suivante avec la valeur souhaitée au fichier *.runtimeconfig.json* :

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- Lorsque vous utilisez l' [CLI .net Core](../tools/index.md), ajoutez l’option suivante avec la valeur souhaitée à une commande .net Core, par exemple `run` :

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

L’extrapolation de version de correctif logiciel est indépendante de ce paramètre, et est effectuée une fois que l’éventuelle extrapolation de version mineure ou majeure a été appliquée.

## <a name="deployment"></a>Déploiement

### <a name="self-contained-application-servicing"></a>Maintenance d’une application autonome

`dotnet publish` publie désormais des applications autonomes avec une version de runtime révisée. Lorsque vous publiez une application autonome avec le Kit de développement .NET Core 2.1 (2.1.300), votre application inclut la dernière version du runtime révisée et identifiée par ce SDK. Lorsque vous effectuez une mise à niveau vers le dernier Kit de développement logiciel (SDK), vous publiez avec la dernière version du Runtime .NET Core. Cela s’applique aux runtimes .NET Core 1.0 et versions ultérieures.

La publication autonome s’appuie sur les versions du Runtime sur NuGet.org. Vous n’avez pas besoin du runtime desservi sur votre ordinateur.

À l’aide du Kit de développement logiciel .NET Core 2.0, les applications autonomes sont publiées avec le runtime .NET Core 2.0.0, sauf si une version différente est spécifiée via la propriété `RuntimeFrameworkVersion`. Avec ce nouveau comportement, vous n’avez plus besoin de définir cette propriété pour sélectionner une version de Runtime plus élevée pour une application autonome. Dorénavant, l’approche la plus simple consiste à toujours publier avec le Kit de développement .NET Core 2.1 (2.1.300).

Pour plus d’informations, voir [Restauration par progression du runtime de déploiement autonome](../deploying/runtime-patch-selection.md).
## <a name="windows-compatibility-pack"></a>Pack de compatibilité Windows

Lorsque vous portez du code existant de .NET Framework vers .NET Core, vous pouvez utiliser le [pack de compatibilité Windows](https://www.nuget.org/packages/Microsoft.Windows.Compatibility). Il permet d’accéder aux plus de 20 000 API disponibles dans .NET Core. Ces API incluent les types dans l’espace de noms <xref:System.Drawing?displayProperty=nameWithType>, la classe <xref:System.Diagnostics.EventLog>, WMI, les compteurs de performances, les services Windows, ainsi que les types et membres de registre Windows.

## <a name="jit-compiler-improvements"></a>Améliorations du compilateur JIT

.NET Core intègre une nouvelle technologie de compilateur JIT appelée *compilation à plusieurs niveaux* (ou également *optimisation adaptative*), qui peut améliorer considérablement les performances. La compilation à plusieurs niveaux n’est pas activée par défaut.

Une des tâches importantes effectuées par le compilateur JIT est l’optimisation de l’exécution du code. Toutefois, pour les chemins de code peu utilisés, le compilateur peut passer plus de temps à optimiser le code que le runtime passe à exécuter du code non optimisé. La compilation à plusieurs niveaux ajoute deux étapes à la compilation JIT :

- Un **premier niveau**, qui génère du code aussi rapidement que possible.

- Un **second niveau**, qui génère un code optimisé pour les méthodes fréquemment exécutées. Le second niveau de compilation est effectué en parallèle pour améliorer les performances.

Vous pouvez activer la compilation à plusieurs niveaux de deux manières.

- Pour utiliser la compilation à plusieurs niveaux dans tous les projets qui utilisent le Kit de développement .NET Core 2.1, définissez la variable d’environnement suivante :

  ```console
  COMPlus_TieredCompilation="1"
  ```

- Pour utiliser la compilation à plusieurs niveaux par projet, ajoutez la propriété `<TieredCompilation>` à la section `<PropertyGroup>` du fichier projet MSBuild, comme le montre l’exemple suivant :

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a>Modifications d'API

### <a name="spant-and-memoryt"></a>`Span<T>` et `Memory<T>`

.NET Core 2.1 inclut certains nouveaux types qui facilitent l’utilisation de tableaux et d’autres types de mémoire beaucoup plus efficaces. Ces nouveaux types incluent :

- <xref:System.Span%601?displayProperty=nameWithType> et <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType> et <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Sans ces types, lorsque vous passez des éléments de ce type comme une partie d’un tableau ou d’une section d’une mémoire tampon, vous devez créer une copie d’une partie des données avant de les passer à une méthode. Ces types fournissent une représentation virtuelle des données, qui supprime les opérations supplémentaires d’allocation de mémoire et de copie.

L’exemple suivant utilise une instance <xref:System.Span%601> et <xref:System.Memory%601> pour fournir une représentation virtuelle de 10 éléments d’un tableau.

[!code-csharp[Span\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/program.cs)]

[!code-vb[Memory\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a>Compression de Brotli

.NET Core 2.1 prend en charge la compression et la décompression de Brotli. Brotli est un algorithme de compression sans perte à usage général, défini dans [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt), et pris en charge par la plupart des navigateurs web et les principaux serveurs web. Vous pouvez utiliser une classe <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> basée sur les flux ou des classes hautes performances <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> et <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> basées sur la portée. L'exemple suivant montre une compression avec la classe <xref:System.IO.Compression.BrotliStream> :

[!code-csharp[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

Le comportement de <xref:System.IO.Compression.BrotliStream> est identique à <xref:System.IO.Compression.DeflateStream> et <xref:System.IO.Compression.GZipStream>, ce qui facilite la convertir du code qui appelle ces API pour <xref:System.IO.Compression.BrotliStream>.

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Nouvelles API de chiffrement et améliorations du chiffrement

.NET Core 2.1 inclut de nombreuses améliorations des API de chiffrement :

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> est disponible dans le package System.Security.Cryptography.Pkcs. L’implémentation est identique à la classe <xref:System.Security.Cryptography.Pkcs.SignedCms> du .NET Framework.

- De nouvelles surcharges des méthodes <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> et <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> acceptent un identificateur d’algorithme de hachage permettant aux appelants d’obtenir les valeurs d’empreinte numérique de certificat à l’aide d’algorithmes autres que SHA-1.

- De nouvelles API de chiffrement basées sur <xref:System.Span%601> sont disponibles pour le hachage, HMAC, la génération de codes de chiffrement aléatoires, la génération de signatures asymétriques, le traitement de signatures asymétriques et le chiffrement RSA.

- Les performances de <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> ont été améliorées d’environ 15 % grâce à une implémentation <xref:System.Span%601>.

- La nouvelle classe <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> inclut deux nouvelles méthodes :

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> prend une quantité fixe de temps pour renvoyer deux entrées de même longueur, ce qui permet de l’utiliser dans une vérification du chiffrement afin d’éviter la temporisation des informations sur le canal auxiliaire.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> est une routine de nettoyage de la mémoire qui ne peut pas être optimisée.

- La méthode statique <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> remplit <xref:System.Span%601> de valeurs aléatoires.

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType>Est désormais pris en charge sur Linux et MacOS.

- Diffie-Hellman à courbe elliptique (ECDH) est désormais disponible dans la famille de classe <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType>. La surface d’exposition est la même que dans le .NET Framework.

- L’instance retournée par <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> peut chiffrer ou déchiffrer avec OAEP à l’aide d’un condensat SHA-2, et permet de générer ou de valider des signatures à l’aide de RSA-PSS.

### <a name="sockets-improvements"></a>Améliorations des sockets

.NET Core inclut un nouveau type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, et une <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType> réécrite, qui constituent la base des API de mise en réseau de niveau supérieur.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, par exemple, est la base de l’implémentation <xref:System.Net.Http.HttpClient>. Dans les versions précédentes de .NET Core, les API de niveau supérieur étaient basées sur des implémentations de mise en réseau natives.

L’implémentation de sockets introduite dans .NET Core 2.1 présente plusieurs avantages :

- Une amélioration significative des performances par rapport à l’implémentation précédente.

- La suppression des dépendances de plateforme, qui simplifie le déploiement et la maintenance.

- Comportement cohérent sur toutes les plates-formes .NET Core.

<xref:System.Net.Http.SocketsHttpHandler> est l’implémentation par défaut dans .NET Core 2.1. Toutefois, vous pouvez configurer votre application pour utiliser l’ancienne classe <xref:System.Net.Http.HttpClientHandler> en appelant la méthode <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> :

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

Vous pouvez également utiliser une variable d’environnement pour désactiver l’utilisation des implémentations de sockets basées sur <xref:System.Net.Http.SocketsHttpHandler>. Pour cela, définissez `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` sur `false` ou 0.

Sous Windows, vous pouvez également choisir d’utiliser <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, repose sur une implémentation native, ou la classe <xref:System.Net.Http.SocketsHttpHandler> en passant une instance de la classe au constructeur <xref:System.Net.Http.HttpClient>.

Sous Linux et macOS, vous pouvez uniquement configurer <xref:System.Net.Http.HttpClient> par processus. Sous Linux, vous devez déployer [libcurl](https://curl.haxx.se/libcurl/) si vous souhaitez utiliser l’ancienne implémentation <xref:System.Net.Http.HttpClient>. (Il est installé avec .NET Core 2.0.)

### <a name="breaking-changes"></a>Changements cassants

Pour plus d’informations sur les modifications avec rupture, consultez [modifications avec rupture pour la migration de la version 2,0 vers 2,1](../compatibility/2.0-2.1.md).

## <a name="see-also"></a>Voir aussi

- [Nouveautés de .NET Core 3.1](dotnet-core-3-1.md)
- [Nouvelles fonctionnalités d’EF Core 2.1](/ef/core/what-is-new/ef-core-2.1)
- [Nouveautés d’ASP.NET Core 2.1](/aspnet/core/aspnetcore-2.1)
