---
title: Meilleures pratiques pour le chargement d'assembly
description: Explorez les meilleures pratiques pour le chargement d’assembly dans .NET. Évitez les problèmes d’identité de type qui peuvent entraîner des casts non valides, des méthodes manquantes et d’autres exceptions.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies,binding
- LoadFrom method
- default load context
- TypeLoadException class,causes
- assembly loading errors
- load contexts
- assemblies,loading
- LoadWithPartialName method
- load-from context
ms.assetid: 68d1c539-6a47-4614-ab59-4b071c9d4b4c
ms.openlocfilehash: 9e09c9e43a4bd8b13712d5fbbf85830394ac0b58
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236440"
---
# <a name="best-practices-for-assembly-loading"></a>Meilleures pratiques pour le chargement d'assembly

Cet article explique les moyens d’éviter les problèmes d’identités de type qui peuvent générer des exceptions <xref:System.InvalidCastException> et <xref:System.MissingMethodException>, et d’autres erreurs. L’article aborde les recommandations suivantes :  
  
- [Comprendre les avantages et les inconvénients des contextes de chargement](#load_contexts)  
  
- [Éviter la liaison sur les noms d’assemblys partiels](#avoid_partial_names)  
  
- [Éviter de charger un assembly dans plusieurs contextes](#avoid_loading_into_multiple_contexts)  
  
- [Éviter de charger plusieurs versions d’un assembly dans le même contexte](#avoid_loading_multiple_versions)  
  
- [Envisager de basculer vers le contexte de chargement par défaut](#switch_to_default)  
  
 La première recommandation, [comprendre les avantages et inconvénients des contextes de chargement](#load_contexts), fournit des informations générales pour les autres recommandations, car elles dépendent toutes d’une connaissance des contextes de chargement.  
  
<a name="load_contexts"></a>

## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Comprendre les avantages et les inconvénients des contextes de chargement  

 Dans un domaine d’application, les assemblys peuvent être chargés dans un contexte parmi trois, ou peuvent être chargés sans contexte :  
  
- Le contexte de chargement par défaut contient les assemblys trouvés en recherchant dans le Global Assembly Cache, dans le magasin d’assemblys de l’hôte si le runtime est hébergé (par exemple dans SQL Server), et dans le <xref:System.AppDomainSetup.ApplicationBase%2A> et le <xref:System.AppDomainSetup.PrivateBinPath%2A> du domaine d’application. La plupart des surcharges de la méthode <xref:System.Reflection.Assembly.Load%2A> chargent les assemblys dans ce contexte.  
  
- Le contexte de chargement source contient des assemblys chargés à partir d’emplacements où le chargeur ne fait pas de recherche. Par exemple, des compléments peuvent être installés dans un répertoire qui n’est pas sous le chemin de l’application. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType> et <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> sont des exemples de méthodes qui sont chargées via un chemin.  
  
- Le contexte de réflexion uniquement contient des assemblys chargés avec les méthodes <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> et <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>. Le code de ce contexte ne peut pas être exécuté et il n’est donc pas abordé ici. Pour plus d’informations, consultez [Guide pratique pour charger des assemblys dans le contexte de réflexion uniquement](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
- Si vous avez généré un assembly dynamique transitoire en utilisant l’émission par réflexion, l’assembly ne se trouve dans aucun contexte. En outre, la plupart des assemblys chargés à l’aide de la méthode <xref:System.Reflection.Assembly.LoadFile%2A> sont chargés sans contexte, et les assemblys qui sont chargés à partir de tableaux d’octets sont chargés sans contexte, à moins que leur identité (une fois que la stratégie est appliquée) établisse qu’ils se trouvent dans le Global Assembly Cache.  
  
 Les contextes d’exécution présentent des avantages et des inconvénients, qui sont présentés dans les sections suivantes.  
  
### <a name="default-load-context"></a>Contexte de chargement par défaut  

 Quand les assemblys sont chargés dans le contexte de chargement par défaut, leurs dépendances sont chargées automatiquement. Les dépendances qui sont chargées dans le contexte de chargement par défaut sont trouvées automatiquement pour les assemblys dans le contexte de chargement par défaut ou dans le contexte de chargement source. Le chargement par identité d’assembly augmente la stabilité des applications en vérifiant que des versions inconnues des assemblys ne sont pas utilisées (consultez la section [Éviter la liaison sur les noms d’assemblys partiels](#avoid_partial_names)).  
  
 L’utilisation du contexte de chargement par défaut a les inconvénients suivants :  
  
- Les dépendances chargées dans d’autres contextes ne sont pas disponibles.  
  
- Vous ne pouvez pas charger des assemblys à partir d’emplacements qui sont en dehors du chemin de recherche dans le contexte de chargement par défaut.  
  
### <a name="load-from-context"></a>Contexte de chargement source  

 Le contexte de chargement source vous permet de charger un assembly à partir d’un chemin qui n’est pas sous le chemin de l’application et qui n’est par conséquent pas inclus dans la recherche. Il permet la localisation et le chargement des dépendances à partir de ce chemin, car les informations du chemin sont gérées par le contexte. En outre, les assemblys de ce contexte peuvent utiliser les dépendances qui sont chargées dans le contexte de chargement par défaut.  
  
 Le chargement des assemblys à l’aide de la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> ou de l’une des autres méthodes qui chargent via un chemin a les inconvénients suivants :  
  
- Si un assembly avec la même identité est déjà chargé dans le contexte Load-from, <xref:System.Reflection.Assembly.LoadFrom%2A> retourne l’assembly chargé même si un autre chemin d’accès a été spécifié.  
  
- Si un assembly est chargé avec <xref:System.Reflection.Assembly.LoadFrom%2A> et qu’ultérieurement, un assembly du contexte de chargement par défaut essaie de charger le même assembly via le nom d’affichage, la tentative de chargement échoue. Ceci peut se produire quand un assembly est désérialisé.  
  
- Si un assembly est chargé avec <xref:System.Reflection.Assembly.LoadFrom%2A> et que le chemin de recherche inclut un assembly avec la même identité mais à un emplacement différent, une <xref:System.InvalidCastException>, <xref:System.MissingMethodException> ou un autre comportement inattendu peut se produire.  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A> demande <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> et <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType>, ou <xref:System.Net.WebPermission>, sur le chemin spécifié.  
  
- S’il existe une image native pour l’assembly, elle n’est pas utilisée.  
  
- L’assembly ne peut pas être chargé comme étant indépendant du domaine.  
  
- Dans les versions 1.0 et 1.1 du .NET Framework, la stratégie n’est pas appliquée.  
  
### <a name="no-context"></a>Pas de contexte  

 Le chargement sans contexte est la seule option pour les assemblys transitoires générés avec l’émission par réflexion. Le chargement sans contexte est la seule façon de charger plusieurs assemblys qui ont la même identité dans un même domaine d’application. Ceci permet d’éviter le coût lié à la recherche.  
  
 Les assemblys chargés à partir de tableaux d’octets sont chargés sans contexte, sauf si l’identité de l’assembly, qui est établie quand la stratégie est appliquée, correspond à l’identité d’un assembly dans le Global Assembly Cache. Dans ce cas, l’assembly est chargé à partir du Global Assembly Cache.  
  
 Le chargement d’assemblys sans contexte a les inconvénients suivants :  
  
- D’autres assemblys ne peuvent pas se lier aux assemblys qui sont chargés sans contexte, sauf si vous gérez l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.  
  
- Les dépendances ne sont pas chargées automatiquement. Vous pouvez les précharger sans contexte, les précharger dans le contexte de chargement par défaut ou les charger en gérant l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.  
  
- Le chargement de plusieurs assemblys avec la même identité sans contexte peut provoquer des problèmes d’identité de type similaires à ceux provoqués par le chargement d’assemblys avec la même identité dans plusieurs contextes. Consultez [Éviter de charger un assembly dans plusieurs contextes](#avoid_loading_into_multiple_contexts).  
  
- S’il existe une image native pour l’assembly, elle n’est pas utilisée.  
  
- L’assembly ne peut pas être chargé comme étant indépendant du domaine.  
  
- Dans les versions 1.0 et 1.1 du .NET Framework, la stratégie n’est pas appliquée.  
  
<a name="avoid_partial_names"></a>

## <a name="avoid-binding-on-partial-assembly-names"></a>Éviter la liaison sur les noms d’assemblys partiels  

 Une liaison de nom partiel se produit quand vous ne spécifiez qu’une partie du nom d’affichage de l’assembly (<xref:System.Reflection.Assembly.FullName%2A>) quand vous chargez un assembly. Par exemple, vous pouvez appeler la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> avec seulement le nom simple de l’assembly, en omettant la version, la culture et le jeton de clé publique. Vous pouvez aussi appeler la méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>, qui appelle d’abord la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> et qui, en cas d’échec de la localisation de l’assembly, recherche dans le Global Assembly Cache et charge la dernière version disponible de l’assembly.  
  
 Une liaison de nom partiel peut provoquer de nombreux problèmes, notamment les suivants :  
  
- La méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> peut charger un autre assembly portant le même nom simple. Par exemple, deux applications peuvent installer deux assemblys complètement différents qui ont tous deux le nom simple `GraphicsLibrary` dans le Global Assembly Cache.  
  
- L’assembly qui est actuellement chargé risque de ne pas être à compatibilité descendante. Par exemple, le fait de ne pas spécifier la version risque d’aboutir au chargement d’une version beaucoup plus récente que la version pour laquelle votre programme a été écrit à l’origine. Des modifications dans la version plus récente peuvent provoquer des erreurs dans votre application.  
  
- L’assembly qui est actuellement chargé risque de ne pas être à compatibilité ascendante. Par exemple, vous pouvez avoir généré et testé votre application avec la version la plus récente d’un assembly, mais une liaison partielle peut charger une version beaucoup plus ancienne où des fonctionnalités utilisées par votre application sont absentes.  
  
- L’installation de nouvelles applications peut endommager des applications existantes. Une application qui utilise la méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A> peut être endommagée en raison de l’installation d’une version plus récente et incompatible d’un assembly partagé.  
  
- Le chargement d’une dépendance inattendue peut se produire. Si vous chargez deux assemblys qui partagent une dépendance, leur chargement avec une liaison partielle peut aboutir à ce qu’un assembly utilise un composant avec lequel il n’a pas été généré ou testé.  
  
 En raison des problèmes qu’elle peut provoquer, la méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A> a été marquée comme étant dépréciée. Nous vous recommandons d’utiliser à la place la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> et de spécifier des noms d’affichage d’assemblys complets. Consultez [Comprendre les avantages et les inconvénients des contextes de chargement](#load_contexts) et [Envisager de basculer vers le contexte de chargement par défaut](#switch_to_default).  
  
 Si vous voulez utiliser la méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A> car elle facilite le chargement des assemblys, prenez en compte le fait que si votre application échoue avec un message d’erreur qui identifie l’assembly manquant, ceci est probablement susceptible de fournir une meilleure expérience utilisateur, au contraire de l’utilisation automatique d’une version inconnue de l’assembly, qui peut entraîner des failles de sécurité et un comportement imprévisible.  
  
<a name="avoid_loading_into_multiple_contexts"></a>

## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Éviter de charger un assembly dans plusieurs contextes  

 Le chargement d’un assembly dans plusieurs contextes peut provoquer des problèmes d’identités de type. Si le même type est chargé à partir du même assembly dans deux contextes différents, c’est comme si deux types différents du même nom avaient été chargés. Une <xref:System.InvalidCastException> est levée si vous essayez d’effectuer un cast d’un type à l’autre, avec un message trompeur, selon lequel le type `MyType` ne peut pas être converti en type `MyType`.  
  
 Par exemple, supposons que l’interface `ICommunicate` est déclarée dans un assembly nommé `Utility`, qui est référencé par votre programme et aussi par d’autres assemblys chargés par votre programme. Ces autres assemblys contiennent des types qui implémentent l’interface `ICommunicate`, permettant à votre programme de les utiliser.  
  
 Considérez à présent ce qui se passe quand votre programme est exécuté. Les assemblys référencés par votre programme sont chargés dans le contexte de chargement par défaut. Si vous chargez un assembly cible via son identité en utilisant la méthode <xref:System.Reflection.Assembly.Load%2A>, elle sera dans le contexte de chargement par défaut, comme le seront ses dépendances. Votre programme et l’assembly cible utilisent le même assembly `Utility`.  
  
 Supposez cependant que vous chargez l’assembly cible via son chemin de fichier en utilisant la méthode <xref:System.Reflection.Assembly.LoadFile%2A>. L’assembly est chargé sans aucun contexte, et ses dépendances ne sont donc pas chargées automatiquement. Vous pouvez avoir un gestionnaire pour l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> pour fournir la dépendance, et il peut charger l’assembly `Utility` sans contexte à l’aide de la méthode <xref:System.Reflection.Assembly.LoadFile%2A>. Quand vous créez une instance d’un type qui est contenu dans l’assembly cible et que vous essayez de l’affecter à une variable de type `ICommunicate`, une <xref:System.InvalidCastException> est levée, car le runtime considère que les interfaces `ICommunicate` dans les deux copies de l’assembly `Utility` sont des types différents.  
  
 Il existe de nombreux autres scénarios dans lesquels un assembly peut être chargé dans plusieurs contextes. La meilleure approche consiste à éviter les conflits en déplaçant l’assembly cible dans le chemin de votre application et en utilisant la méthode <xref:System.Reflection.Assembly.Load%2A> avec le nom d’affichage complet. L’assembly est ensuite chargé dans le contexte de chargement par défaut, et les deux assemblys utilisent le même assembly `Utility`.  
  
 Si l’assembly cible doit rester en dehors du chemin de votre application, vous pouvez utiliser la méthode <xref:System.Reflection.Assembly.LoadFrom%2A> pour le charger dans le contexte de chargement source. Si l’assembly cible a été compilé avec une référence à l’assembly `Utility` de votre application, il utilisera l’assembly `Utility` que votre application a chargé dans le contexte de chargement par défaut. Notez que des problèmes peuvent se produire si l’assembly cible a une dépendance d’une copie de l’assembly `Utility` qui se trouve en dehors du chemin de votre application. Si cet assembly est chargé dans le contexte de chargement source avant que votre application ne charge l’assembly `Utility`, le chargement de votre application échoue.  
  
 La section [Envisager de basculer vers le contexte de chargement par défaut](#switch_to_default) traite des alternatives à l’utilisation des chargements via un chemin de fichier, comme <xref:System.Reflection.Assembly.LoadFile%2A> et <xref:System.Reflection.Assembly.LoadFrom%2A>.  
  
<a name="avoid_loading_multiple_versions"></a>

## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Éviter de charger plusieurs versions d’un assembly dans le même contexte  

 Le chargement de plusieurs versions d’un assembly dans un même contexte de chargement peut provoquer des problèmes d’identité de type. Si le même type est chargé à partir de deux versions du même assembly, c’est comme si deux types différents du même nom avaient été chargés. Une <xref:System.InvalidCastException> est levée si vous essayez d’effectuer un cast d’un type à l’autre, avec un message trompeur, selon lequel le type `MyType` ne peut pas être converti en type `MyType`.  
  
 Par exemple, votre programme peut charger directement une version de l’assembly `Utility`, et il peut charger ultérieurement un autre assembly qui charge une version différente de l’assembly `Utility`. De même, une erreur de codage peut faire que deux chemins de code différents dans votre application chargent des versions différentes d’un assembly.  
  
 Dans le contexte de chargement par défaut, ce problème peut se produire quand vous utilisez la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> et que vous spécifiez des noms d’affichage d’assemblys complets qui incluent des numéros de version différents. Pour les assemblys chargés sans contexte, le problème peut être dû à l’utilisation de la méthode <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> pour charger le même assembly à partir de différents chemins. Le runtime considère deux assemblys chargés à partir de chemins différents comme des assemblys différents, même si leurs identités sont les mêmes.  
  
 En plus des problèmes d’identités de type, plusieurs versions d’un même assembly peuvent provoquer une <xref:System.MissingMethodException> si un type qui est chargé à partir d’une version de l’assembly est passé au code qui attend ce type d’une autre version. Par exemple, le code peut attendre une méthode qui a été ajoutée à la version ultérieure.  
  
 Des erreurs plus subtiles peuvent se produire si le comportement du type a changé entre les versions. Par exemple, une méthode peut lever une exception inattendue ou retourner une valeur inattendue.  
  
 Examinez soigneusement votre code pour vérifier qu’une seule version d’un assembly est chargée. Vous pouvez utiliser la méthode <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> pour déterminer quels assemblys sont chargés à un moment donné.  
  
<a name="switch_to_default"></a>

## <a name="consider-switching-to-the-default-load-context"></a>Envisager de basculer vers le contexte de chargement par défaut  

 Examinez les modèles de chargement et de déploiement des assemblys de votre application. Pouvez-vous éliminer des assemblys chargés à partir de tableaux d’octets ? Pouvez-vous déplacer des assemblys dans le chemin de recherche ? Si les assemblys se trouvent dans le Global Assembly Cache ou dans le chemin de recherche du domaine d’application (autrement dit son <xref:System.AppDomainSetup.ApplicationBase%2A> et son <xref:System.AppDomainSetup.PrivateBinPath%2A>), vous pouvez charger l’assembly via son identité.  
  
 S’il n’est pas possible de placer tous vos assemblys dans le chemin de recherche, considérez les solutions alternatives, comme utiliser le modèle de complément du .NET Framework, placer les assemblys dans le Global Assembly Cache ou créer des domaines d’application.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>Envisager d’utiliser le modèle de complément du .NET Framework  

 Si vous utilisez le contexte de chargement source pour implémenter des compléments, qui ne sont généralement pas installés dans la base de l’application, utilisez le modèle de complément du .NET Framework. Ce modèle fournit une isolation au niveau du domaine d’application ou du processus, sans qu’il soit nécessaire de gérer vous-même les domaines d’application. Pour plus d’informations sur le modèle de complément, consultez [Compléments et extensibilité](/previous-versions/dotnet/netframework-4.0/bb384200(v=vs.100)).  
  
### <a name="consider-using-the-global-assembly-cache"></a>Envisager d’utiliser le Global Assembly Cache  

 Placez les assemblys dans le Global Assembly Cache pour bénéficier d’un chemin d’assembly partagé qui est en dehors de l’application de base, sans perdre les avantages du contexte de chargement par défaut ou subir les inconvénients des autres contextes.  
  
### <a name="consider-using-application-domains"></a>Envisager d’utiliser des domaines d’application  

 Si vous déterminez que certains de vos assemblys ne peuvent pas être déployés dans le chemin de recherche de l’application, envisagez de créer un domaine d’application pour ces assemblys. Utilisez <xref:System.AppDomainSetup> pour créer le domaine d’application, et utilisez <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> pour spécifier le chemin qui contient les assemblys que vous voulez charger. Si vous avez plusieurs répertoires où rechercher, vous pouvez définir <xref:System.AppDomainSetup.ApplicationBase%2A> sur un répertoire racine et utiliser la propriété <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> pour identifier les sous-répertoires où rechercher. Vous pouvez aussi créer plusieurs domaines d’application et définir <xref:System.AppDomainSetup.ApplicationBase%2A> pour chaque domaine d’application sur le chemin approprié pour ses assemblys.  
  
 Notez que vous pouvez utiliser la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> pour charger ces assemblys. Comme ils sont maintenant dans le chemin de recherche, ils seront chargés dans le contexte de chargement par défaut au lieu du contexte de chargement source. Cependant, nous vous recommandons de passer à la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> et de spécifier des noms d’affichage d’assemblys complets pour garantir que les versions correctes sont toujours utilisées.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>
