---
title: Compilation et .NET natif
ms.date: 03/30/2017
ms.assetid: e38ae4f3-3e3d-42c3-a4b8-db1aa9d84f85
ms.openlocfilehash: cf5c9f05b2f2cb4ca15e4add5b53bc9bdca757a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128248"
---
# <a name="net-native-and-compilation"></a>Compilation et .NET natif

Les applications Windows 8.1 et les applications de bureau Windows qui ciblent le .NET Framework sont écrites dans un langage de programmation particulier et compilées dans un langage intermédiaire. Lors de l'exécution, un compilateur juste-à-temps (JIT) est chargé de compiler du langage intermédiaire en code natif pour l'ordinateur local, juste avant qu'une méthode ne soit exécutée pour la première fois. À l'inverse, la chaîne d'outils .NET Native convertit le code source en code natif au moment de la compilation. Cette rubrique compare .NET Native avec d'autres technologies de compilation disponibles pour les applications .NET Framework. Elle explique également de façon pratique comment .NET Native génère le code natif qui peut vous aider à comprendre pourquoi les exceptions qui se produisent dans le code compilé avec .NET Native ne se produisent pas dans le code compilé par le compilateur JIT.

## <a name="net-native-generating-native-binaries"></a>.NET Native : générer des binaires natifs

Une application qui cible .NET Framework et qui n'est pas compilée à l'aide de la chaîne d'outils .NET Native se compose de votre assembly d'application, qui comprend les éléments suivants :

- Des [métadonnées](../../standard/metadata-and-self-describing-components.md) qui décrivent l’assembly, ses dépendances, les types qu’il contient et leurs membres. Les métadonnées sont utilisées pour la réflexion et l'accès à liaison tardive et dans certains cas, par le compilateur et les outils de génération.

- Du code d'implémentation. Il s’agit des opcodes de langage intermédiaire. Lors de l'exécution, le compilateur juste-à-temps (JIT) le traduit en code natif pour la plateforme cible.

 En plus de votre assembly d'application principal, une application requiert les éléments suivants :

- Toute bibliothèque de classes supplémentaire ou assembly tiers requis par votre application. De même, ces assemblys incluent des métadonnées qui décrivent l'assembly, ses types et leurs membres, ainsi que le langage intermédiaire qui implémente tous les membres de type.

- La bibliothèque de classes .NET Framework. Il s’agit d’une collection d’assemblys qui est installée sur le système local avec l’installation de .NET Framework. Les assemblys inclus dans la bibliothèque de classes .NET Framework comprennent un ensemble complet de métadonnées et de code d'implémentation.

- Le common language runtime. Il s’agit d’une collection de bibliothèques de liens dynamiques qui fournissent des services tels que le chargement des assemblys, la gestion de la mémoire et des garbage collection, la gestion des exceptions, la compilation juste-à-temps, la communication à distance et l’interopérabilité. Tout comme la bibliothèque de classes, le runtime est installé sur le système local dans le cadre de l'installation .NET Framework.

Notez que l'ensemble du common language runtime, ainsi que les métadonnées et le langage intermédiaire de tous les types contenus dans les assemblys spécifiques à l'application, les assemblys tiers et les assemblys système doivent être présents pour que l'application fonctionne correctement.

## <a name="net-native-and-just-in-time-compilation"></a>.NET Native et compilation juste-à-temps

L'entrée de la chaîne d'outils .NET Native est l'application du Windows Store créée par le compilateur C# ou Visual Basic. En d'autres termes, la chaîne d'outils .NET Native commence l'exécution quand le compilateur de langage a terminé la compilation d'une application du Windows Store.

> [!TIP]
> Étant donné que l'entrée de .NET Native correspond au langage intermédiaire et aux métadonnées écrites dans les assemblys managés, vous pouvez toujours effectuer la génération de code personnalisée ou d'autres opérations personnalisées à l'aide d'événements pré-build ou post-build, ou en modifiant le fichier projet MSBuild.
>
> Toutefois, les catégories d'outils qui modifient le langage intermédiaire, et empêchent ainsi la chaîne d'outils .NET d'analyser le langage intermédiaire d'une application, ne sont pas prises en charge. Les obfuscateurs sont les outils de ce type les plus connus.

Au cours de la conversion d'une application du langage intermédiaire en code natif, la chaîne d'outils .NET Native effectue des opérations telles que les suivantes :

- Pour certains chemins de code, elle remplace le code qui s’appuie sur la réflexion et les métadonnées par du code natif statique. Par exemple, si un type valeur ne remplace pas la méthode <xref:System.ValueType.Equals%2A?displayProperty=nameWithType>, le test d'égalité par défaut utilise la réflexion pour récupérer les objets <xref:System.Reflection.FieldInfo> qui représentent les champs du type valeur, puis compare les valeurs de champ des deux instances. Lors de la compilation en code natif, la chaîne d'outils .NET Native remplace le code et les métadonnées de réflexion par une comparaison statique des valeurs de champ.

- Quand cela est possible, elle tente d'éliminer toutes les métadonnées.

- Elle inclut dans les assemblys de l'application finale uniquement le code d'implémentation qui est réellement appelé par l'application. Cela affecte particulièrement le code des bibliothèques tierces et de la bibliothèque de classes .NET Framework. Une application ne dépend donc plus des bibliothèques tierces ni de la bibliothèque de classes .NET Framework complète. Au lieu de cela, le code des bibliothèques tierces et des bibliothèques de classes .NET Framework est désormais local pour l'application.

- Elle remplace le CLR complet par un runtime refactorisé contenant principalement le garbage collector. Le runtime refactorisé se trouve dans une bibliothèque nommée mrt100_app.dll qui est locale pour l'application et dont la taille ne dépasse pas quelques centaines de kilo-octets. Ceci est possible parce que la liaison statique rend inutiles la plupart des services fournis par le common language runtime.

  > [!NOTE]
  > .NET Native utilise le même garbage collector en tant que common language runtime standard. Dans le garbage collector .NET Native, le garbage collection d'arrière-plan est activé par défaut. Pour plus d’informations sur le garbage collection, consultez [Notions de base du garbage collection](../../standard/garbage-collection/fundamentals.md).

> [!IMPORTANT]
> .NET Native compile une application entière en une application native. Il ne vous permet pas de compiler en code natif un assembly unique contenant une bibliothèque de classes pour que celui-ci puisse être appelé de manière autonome depuis le code managé.

L’application résultante produite par la chaîne d’outils .NET Native est écrite dans un répertoire nommé ilc.out, lui-même situé dans le répertoire Debug ou Release de votre répertoire de projet. Elle se compose des fichiers suivants :

- *\<appName>*. exe, un exécutable stub qui transfère simplement le contrôle à une `Main` exportation spéciale dans *\<appName>* . dll.

- *\<appName>*. dll, une bibliothèque de liens dynamiques Windows qui contient l’ensemble de votre code d’application, ainsi que le code de la bibliothèque de classes .NET Framework et des bibliothèques tierces sur lesquelles vous avez une dépendance.  Elle contient également le code de prise en charge, tel que le code nécessaire pour interagir avec Windows et sérialiser les objets de votre application.

- mrt100_app.dll, un runtime refactorisé qui fournit des services d’exécution tels que le garbage collection.

 Toutes les dépendances sont capturées par le manifeste APPX de l'application.  En plus des fichiers .exe, .dll et mrt100_app.dll de l'application, qui sont fournis directement avec le package appx, deux autres fichiers sont inclus :

- msvcr140_app.dll, la bibliothèque Runtime C (CRT) utilisée par mrt100_app.dll. Il est fourni par une référence de framework du package.

- mrt100.dll. Cette bibliothèque inclut des fonctions qui peuvent améliorer les performances de mrt100_app.dll, bien que son absence n'empêche pas mrt100_app.dll de fonctionner. Elle est chargée à partir du répertoire system32 sur l'ordinateur local, s'il s'y trouve.

Étant donné que la chaîne d'outils .NET Native ne lie le code d'implémentation à votre application que s'il sait que votre application appelle ce code, les métadonnées ou le code d'implémentation requis dans les scénarios suivants peuvent ne pas être inclus dans votre application :

- Réflexion.

- Appel dynamique ou à liaison tardive

- Sérialisation et désérialisation

- COM Interop

Si le code d'implémentation ou les métadonnées nécessaires sont absents au moment de l'exécution, le runtime .NET Native lève une exception. Vous pouvez éviter ces exceptions et vérifier que la chaîne d’outils .NET Native inclut le code d’implémentation et les métadonnées nécessaires en utilisant un [fichier de directives runtime](runtime-directives-rd-xml-configuration-file-reference.md). Il s’agit d’un fichier XML qui désigne les éléments de programme dont le code d’implémentation ou les métadonnées doivent être disponibles lors de l’exécution, et qui leur attribue une stratégie runtime. Voici le fichier de directives runtime par défaut qui est ajouté à un projet Windows Store compilé par la chaîne d'outils .NET Native :

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>
```

Il permet à tous les types, ainsi qu'à tous leurs membres, dans tous les assemblys de votre package d'application, de faire l'objet d'une réflexion et d'un appel dynamique. Toutefois, il ne le permet pas aux types des assemblys de la bibliothèque de classes .NET Framework. Dans de nombreux cas, cela suffit.

## <a name="net-native-and-ngen"></a>.NET Native et NGEN

Le [générateur d’images natives](../tools/ngen-exe-native-image-generator.md) (NGEN) compile des assemblys en code natif et les installe dans le cache d’images natives sur l’ordinateur local. Toutefois, même si NGEN génère du code natif comme .NET Native, il comporte des différences importantes :

- Si aucune image native n'est disponible pour une méthode particulière, NGEN revient au code juste-à-temps. Cela signifie que les images natives doivent continuer d'inclure les métadonnées et le langage intermédiaire dans le cas où NGEN doive revenir à la compilation juste-à-temps. À l'inverse, .NET Native génère uniquement des images natives et ne revient pas à la compilation juste-à-temps. Seules les métadonnées requises pour certains scénarios d'interopérabilité, de sérialisation et de réflexion doivent donc être conservées.

- NGEN continue à s’appuyer sur le common language runtime complet pour des services tels que le chargement d’assemblys, la communication à distance, l’interopérabilité, la gestion de la mémoire, le garbage collection et, si nécessaire, la compilation JIT. Dans .NET Native, plusieurs de ces services sont soit inutiles (la compilation JIT), soit résolus au moment de la génération, puis incorporés dans l'assembly de l'application. Les services restants, le plus important étant le garbage collection, sont inclus dans un runtime refactorisé beaucoup plus petit nommé mrt100_app.dll.

- Les images NGEN ont tendance à être fragiles. Par exemple, un correctif ou une modification apportée à une dépendance requièrent généralement que les assemblys qui l'utilisent soient également régénérés par NGEN. Ceci est particulièrement vrai pour les assemblys système de la bibliothèque de classes .NET Framework. À l'inverse, .NET Native permet aux applications d'être fournies indépendamment les unes des autres.

## <a name="see-also"></a>Voir aussi

- [Métadonnées et composants autodescriptifs](../../standard/metadata-and-self-describing-components.md)
- [Inside .NET Native (vidéo Channel 9)](https://channel9.msdn.com/Shows/Going+Deep/Inside-NET-Native)
- [Réflexion et .NET Native](reflection-and-net-native.md)
- [Résolution des problèmes généraux liés à .NET Native](net-native-general-troubleshooting.md)
