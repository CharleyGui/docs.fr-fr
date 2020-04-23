---
title: Contexte de schéma XAML par défaut et contexte de schéma XAML WPF
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 2e92372de61230a98a02282cc28fc3f479cd94eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071863"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Contexte de schéma XAML par défaut et contexte de schéma XAML WPF
Un contexte de schéma XAML est une entité conceptuelle qui qualifie la façon dont une production XAML qui utilise un vocabulaire XAML particulier interagit avec le comportement d’écriture d’objets, y compris la façon dont la cartographie de type se résout, comment les assemblages sont chargés, comment certains paramètres de lecteur et d’auteur sont interprétés. Ce sujet décrit les caractéristiques de .NET XAML Services et le contexte de schéma XAML par défaut associé, qui est basé sur le système de type CLR. Ce sujet décrit également le contexte du schéma XAML qui est utilisé pour WPF.

## <a name="default-xaml-schema-context"></a>Contexte XAML Schema par défaut

.NET XAML Services implémente et utilise un contexte de schéma XAML par défaut. Le comportement par défaut du contexte du schéma XAML <xref:System.Xaml.XamlSchemaContext> n’est pas toujours entièrement visible dans l’API de la classe. Cependant, dans de nombreux cas, le comportement que le contexte du schéma XAML par défaut influence est <xref:System.Xaml.XamlMember> observable par l’API commune du système de type XAML, tels que les membres ou , ou <xref:System.Xaml.XamlType>par le biais d’API exposés sur les lecteurs XAML et les écrivains XAML qui utilisent le contexte par défaut de schéma XAML.

Vous pouvez <xref:System.Xaml.XamlSchemaContext> créer un qui encapsule le <xref:System.Xaml.XamlSchemaContext> comportement par défaut en appelant le constructeur. Cela crée explicitement le contexte de schéma XAML par défaut. Le même contexte de schéma XAML par défaut est créé implicitement, si vous initialisez un lecteur <xref:System.Xaml.XamlSchemaContext> XAML ou un auteur XAML utilisant des API qui ne prennent pas explicitement un paramètre d’entrée.

Le contexte de schéma XAML par défaut repose sur la réflexion CLR pour son comportement de cartographie de type. Cela comprend l’examen <xref:System.Type>de <xref:System.Reflection.PropertyInfo> la <xref:System.Reflection.MethodInfo>définition CLR , et connexes ou . En outre, l’attribution CLR sur les types ou les membres est utilisée afin de remplir les détails pour le type XAML ou XAML informations membres qui utilise le type de support CLR. Le contexte par défaut du schéma XAML ne `Invoker` nécessite pas de techniques d’extension de système de type telles que le modèle, parce que les informations nécessaires sont disponibles à partir du système de type CLR.

Pour la logique de chargement d’assemblage, le contexte par défaut du schéma XAML repose principalement sur toutes les valeurs d’assemblage fournies dans les cartographies XAML namespace. En <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> outre, peut laisser entendre un assemblage à charger, pour des scénarios tels que le chargement des types internes.

## <a name="wpf-xaml-schema-context"></a>Contexte WPF XAML Schema

Le contexte du schéma WPF XAML est décrit dans ce sujet parce que la mise en œuvre du WPF fournit une illustration intéressante des types de fonctionnalités qui peuvent être introduites par la mise en œuvre d’un contexte de schéma XAML non par défaut. En outre, le concept de contexte schéma XAML n’est pas beaucoup discuté dans la documentation WPF qui traite WPF XAML; le comportement que le contexte du schéma XAML permet ne peut être pleinement compréhensible que s’il est intégré à une discussion sur le fonctionnement du contexte du schéma XAML par défaut. Le contexte du schéma WPF XAML met en œuvre le comportement suivant.

**Remplacements de recherche :** WPF a quelques modèles de contenu pour XAML où il <xref:System.Windows.Markup.ContentPropertyAttribute> ya des propriétés de contenu XAML qui fonctionnent sans être attribué. <xref:System.Xaml.XamlType.LookupContentProperty%2A>remplacent WPF implémenter ce comportement.

**Report pour les expressions WPF:** WPF dispose de plusieurs classes d’expression qui reportent une valeur jusqu’à ce qu’un contexte de ruissellement soit disponible. En outre, l’expansion du modèle est un comportement de runtime qui repose sur des techniques de report.

**Optimisations de recherche de système de type :** WPF a un vocabulaire XAML étendu et modèle d’objet, y compris les définitions de membres de la classe de base qui héritent de littéralement des centaines de classes définies par WPF. En outre, WPF lui-même est répartie sur plusieurs assemblées. WPF optimise son type de recherche à l’aide de tables de recherche et d’autres techniques. Cela permet d’améliorer les performances sur le contexte du schéma XAML par défaut et sa recherche de type CLR. Dans les cas où les types n’existent pas dans un tableau de recherche, le comportement utilise XAML techniques de contexte schéma qui sont similaires au contexte de schéma XAML par défaut.

**Extension XamlType et XamlMember :** WPF étend les concepts de propriété avec des propriétés de dépendance, et les concepts d’événements avec des événements acheminés. Pour donner à ces concepts une plus grande <xref:System.Xaml.XamlType> visibilité <xref:System.Xaml.XamlMember>pour les opérations de traitement XAML, WPF s’étend et, et ajoute des propriétés internes qui signalent la propriété de dépendance et les caractéristiques d’événements acheminées.

### <a name="accessing-the-wpf-xaml-schema-context"></a>Accès au contexte WPF XAML Schema

Si vous utilisez des techniques XAML qui <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>sont basées sur le WPF ou , le contexte WPF XAML schéma est déjà utilisé sur ces implémentations XAML lecteur et écrivain XAML.

Si vous utilisez d’autres implémentations de lecteur XAML ou d’auteur XAML qui ne sont pas parassables avec <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>le contexte du schéma WPF XAML, vous pouvez être en mesure d’obtenir un contexte de schéma WPF XAML de travail à partir de . Vous pouvez ensuite utiliser cette valeur comme initialisation <xref:System.Xaml.XamlSchemaContext>pour d’autres API qui utilisent un . Par exemple, vous <xref:System.Xaml.XamlXmlReader.%23ctor%2A> pouvez appeler à l’initialisation et passer le contexte du schéma WPF XAML. Ou vous pouvez utiliser le contexte du schéma WPF XAML pour les opérations du système de type XAML. Cela peut inclure l’initialisation de construction d’un <xref:System.Xaml.XamlType> ou <xref:System.Xaml.XamlMember>, ou d’appeler <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>.

Notez que si vous accédez à certains aspects de WPF XAML à partir d’un simple Nœud XAML perspectives flux, certaines des capacités de cadre WPF peut ne pas avoir agi encore. Par exemple, les modèles WPF pour les contrôles ne sont pas encore appliqués. Ainsi, si vous accédez à une propriété qui, à l’heure de l’exécution, peut être peuplée d’un arbre visuel complet, vous ne pouvez voir qu’une valeur de propriété qui fait référence à un modèle. Le contexte de service prévu pour les extensions de balisage WPF peut également ne pas être exact s’il est fourni à partir d’une situation non-runtime, et peut entraîner des exceptions lors de la tentative d’écrire un graphique d’objet.

## <a name="xaml-and-assembly-loading"></a>Chargement XAML et Assemblage

Le chargement d’assemblage pour XAML et .NET XAML <xref:System.AppDomain>Services s’intègre au concept défini par CLR de . Un contexte de schéma XAML interprète comment charger des assemblages ou trouver des types <xref:System.AppDomain> au moment de l’exécution ou au moment de la conception, en fonction de l’utilisation et d’autres facteurs. La logique est légèrement différente selon que le XAML est lâche XAML pour un lecteur `XamlBuildTask`XAML, est XAML `PresentationBuildTask`compilé dans un DLL par , ou est BAML généré par WPF .

Le contexte du schéma XAML pour WPF s’intègre au <xref:System.AppDomain> modèle d’application WPF, qui à son tour utilise ainsi que d’autres facteurs qui sont des détails de mise en œuvre WPF.

#### <a name="xaml-reader-input-loose-xaml"></a>Entrée de lecteur XAML (lâche XAML)

01. Le contexte du schéma XAML <xref:System.AppDomain> s’étend à travers l’application, à la recherche d’un assemblage déjà chargé qui correspond à tous les aspects du nom, à partir de l’assemblage le plus récemment chargé. Si une correspondance est trouvée, cette assemblée est utilisée pour la résolution.

02. Dans le cas contraire, l’une des techniques suivantes basées sur l’API CLR <xref:System.Reflection.Assembly> est utilisée pour charger un assemblage :

    - Si le nom est qualifié <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> dans la cartographie, faites appel au nom qualifié.

    - Si l’étape précédente échoue, utilisez le nom court (et <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>le jeton de clé publique si présent) pour appeler .

    - Si le nom n’est pas <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>qualifié dans la cartographie, appelez .

#### <a name="xamlbuildtask"></a>XamlBuildTask

`XamlBuildTask`est utilisé pour Windows Communication Foundation (WCF) et Windows Workflow Foundation.

Notez que `XamlBuildTask` les références d’assemblage à travers sont toujours entièrement qualifiés.

1. Faites <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> appel au nom qualifié.

2. Si l’étape précédente échoue, utilisez le nom court (et <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>le jeton de clé publique si présent) pour appeler .

#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)

Il y a deux aspects au chargement d’assemblage pour BAML : le chargement de l’assemblage initial qui contient le BAML comme composant, et le chargement des assemblages de type-backing pour tous les types référencés par la production BAML.

##### <a name="assembly-load-for-initial-markup"></a>Charge d’assemblage pour la majoration initiale :

La référence à l’assemblage pour charger la majoration à partir est toujours inégalée.

1. Le contexte du schéma WPF XAML <xref:System.AppDomain> s’étend à travers l’application WPF, à la recherche d’un assemblage déjà chargé qui correspond à tous les aspects du nom, à partir de l’assemblage le plus récemment chargé. Si une correspondance est trouvée, cette assemblée est utilisée pour la résolution.

2. Si l’étape précédente échoue, utilisez le nom court (et <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>le jeton de clé publique si présent) pour appeler .

##### <a name="assembly-references-by-baml-types"></a>Références d’assemblage par types BAML :

Les références d’assemblage pour les types utilisés dans la production BAML sont toujours entièrement qualifiées, comme sortie de la tâche de construction.

01. Le contexte du schéma WPF XAML <xref:System.AppDomain> s’étend à travers l’application WPF, à la recherche d’un assemblage déjà chargé qui correspond à tous les aspects du nom, à partir de l’assemblage le plus récemment chargé. Si une correspondance est trouvée, cette assemblée est utilisée pour la résolution.

02. Sinon, l’une des techniques suivantes est utilisée pour charger un assemblage :

    - Faites <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> appel au nom qualifié.
  
    - Si une combinaison de jetons à clé publique de nom court correspond à l’assemblage dont le BAML a été chargé, utilisez cet assemblage.

    - Utilisez le nom court et <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>le jeton de clé publique pour appeler .

## <a name="see-also"></a>Voir aussi

- [Fonctionnement des concepts et structures du flux de nœud XAML](understanding-xaml-node-stream-structures-and-concepts.md)
