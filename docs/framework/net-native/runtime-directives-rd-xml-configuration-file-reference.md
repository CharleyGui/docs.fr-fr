---
title: Guide de référence du fichier de configuration des directives runtime (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: e74d34693446cca645003a9f93bc1777849e3182
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738409"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a>Guide de référence du fichier de configuration des directives runtime (rd.xml)

Un fichier de directives runtime (.rd.xml) est un fichier de configuration XML qui spécifie si les éléments de programme désignés sont disponibles pour la réflexion. Voici un exemple de fichier de directives runtime :

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />
    <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />
    <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />
    <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />

    <Namespace Name="System.Collections.ObjectModel" >
      <TypeInstantiation Name="ObservableCollection"
            Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />
      <TypeInstantiation Name="ReadOnlyObservableCollection"
            Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />
    </Namespace>
  </Application>
</Directives>
```

## <a name="the-structure-of-a-runtime-directives-file"></a>Structure d'un fichier de directives runtime

Le fichier de directives runtime utilise l'espace de noms `http://schemas.microsoft.com/netfx/2013/01/metadata`.

L’élément racine est l’élément [Directives](directives-element-net-native.md). Il peut contenir zéro ou plusieurs éléments [Library](library-element-net-native.md) et zéro ou un élément [Application](application-element-net-native.md), comme indiqué dans la structure suivante. Les attributs de l’élément [Application](application-element-net-native.md) peuvent définir une stratégie de réflexion runtime à l’échelle de l’application, ou peuvent servir de conteneur pour les éléments enfants. L’élément [Library](library-element-net-native.md), quant à lui, sert simplement de conteneur. Les enfants des éléments[Application](application-element-net-native.md) et [Library](library-element-net-native.md) définissent les types, méthodes, champs, propriétés et événements qui sont disponibles pour la réflexion.

Pour obtenir des informations de référence, choisissez les éléments dans la structure suivante ou consultez [Éléments de directive runtime](runtime-directive-elements.md). Dans la hiérarchie suivante, les points de suspension marquent une structure récursive. Les informations entre crochets indiquent si l'élément concerné est facultatif ou obligatoire, et, s'il est utilisé, le nombre d'instances autorisées (une ou plusieurs).

- [Directives](directives-element-net-native.md) [1:1]
  - [Application](application-element-net-native.md) [0:1]
    - [Assembly](assembly-element-net-native.md) [0:M]
      - [Espace de noms](namespace-element-net-native.md) [0 : M]. . .
      - [Tapez](type-element-net-native.md) [0 : M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M]. . .
    - [Namespace](namespace-element-net-native.md) [0:M]
      - [Espace de noms](namespace-element-net-native.md) [0 : M]. . .
      - [Tapez](type-element-net-native.md) [0 : M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M]. . .
    - [Type](type-element-net-native.md) [0:M]
      - [Subtypes](subtypes-element-net-native.md) (sous-classes du type conteneur) [O:1]
      - [Tapez](type-element-net-native.md) [0 : M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M]. . .
      - [AttributeImplies](attributeimplies-element-net-native.md) (le type conteneur est un attribut) [O:1]
      - [GenericParameter](genericparameter-element-net-native.md) [0:M]
      - [Method](method-element-net-native.md) [0:M]
        - [Parameter](parameter-element-net-native.md) [0:M]
        - [TypeParameter](typeparameter-element-net-native.md) [0:M]
        - [GenericParameter](genericparameter-element-net-native.md) [0:M]
      - [MethodInstantiation](methodinstantiation-element-net-native.md) (méthode générique construite) [0:M]
      - [Property](property-element-net-native.md) [0:M]
      - [Field](field-element-net-native.md) [0:M]
      - [Event](event-element-net-native.md) [0:M]
    - [TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0:M]
      - [Tapez](type-element-net-native.md) [0 : M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M]. . .
      - [Method](method-element-net-native.md) [0:M]
        - [Parameter](parameter-element-net-native.md) [0:M]
        - [TypeParameter](typeparameter-element-net-native.md) [0:M]
        - [GenericParameter](genericparameter-element-net-native.md) [0:M]
      - [MethodInstantiation](methodinstantiation-element-net-native.md) (méthode générique construite) [0:M]
      - [Property](property-element-net-native.md) [0:M]
      - [Field](field-element-net-native.md) [0:M]
      - [Event](event-element-net-native.md) [0:M]
  - [Library](library-element-net-native.md) [0:M]
    - [Assembly](assembly-element-net-native.md) [0:M]
      - [Espace de noms](namespace-element-net-native.md) [0 : M]. . .
      - [Tapez](type-element-net-native.md) [0 : M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M]. . .
    - [Namespace](namespace-element-net-native.md) [0:M]
      - [Espace de noms](namespace-element-net-native.md) [0 : M]. . .
      - [Tapez](type-element-net-native.md) [0 : M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M]. . .
    - [Type](type-element-net-native.md) [0:M]
      - [Subtypes](subtypes-element-net-native.md) (sous-classes du type conteneur) [O:1]
      - [Tapez](type-element-net-native.md) [0 : M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M]. . .
      - [AttributeImplies](attributeimplies-element-net-native.md) (le type conteneur est un attribut) [O:1]
      - [GenericParameter](genericparameter-element-net-native.md) [0:M]
      - [Method](method-element-net-native.md) [0:M]
      - [MethodInstantiation](methodinstantiation-element-net-native.md) (méthode générique construite) [0:M]
      - [Property](property-element-net-native.md) [0:M]
      - [Field](field-element-net-native.md) [0:M]
      - [Event](event-element-net-native.md) [0:M]
    - [TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0:M]
      - [Tapez](type-element-net-native.md) [0 : M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (type générique construit) [0 : M]. . .
      - [Method](method-element-net-native.md) [0:M]
      - [MethodInstantiation](methodinstantiation-element-net-native.md) (méthode générique construite) [0:M]
      - [Property](property-element-net-native.md) [0:M]
      - [Field](field-element-net-native.md) [0:M]
      - [Event](event-element-net-native.md) [0:M]

L’élément [Application](application-element-net-native.md) peut n’avoir aucun attribut, ou peut avoir les attributs de stratégie présentés dans la section [Stratégie et directives runtime](#Directives).

Un élément [Library](library-element-net-native.md) possède un attribut unique (`Name`) qui spécifie le nom d’une bibliothèque ou d’un assembly, sans son extension de fichier. Par exemple, l’élément [Library](library-element-net-native.md) suivant s’applique à un assembly nommé Extensions.dll.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <!-- Child elements go here -->
  </Application>
  <Library Name="Extensions">
     <!-- Child elements go here -->
  </Library>
</Directives>
```

<a name="Directives"></a>

## <a name="runtime-directives-and-policy"></a>Stratégie et directives runtime

L’élément [Application](application-element-net-native.md) lui-même et les éléments enfants des éléments [Library](library-element-net-native.md) et [Application](application-element-net-native.md) expriment la stratégie ; autrement dit, ils définissent la façon dont une application peut appliquer la réflexion à un élément de programme. Le type de stratégie est défini par un attribut de l'élément (par exemple, `Serialize`). La valeur de stratégie est définie par la valeur de l'attribut (par exemple, `Serialize="Required"`).

Toute stratégie spécifiée par un attribut d'un élément s'applique à tous les éléments enfants qui ne définissent pas de valeur pour cette stratégie. Par exemple, si une stratégie est spécifiée par un élément [Type](type-element-net-native.md), elle s’applique à tous les types et membres contenus pour lesquels une stratégie n’est pas explicitement définie.

La stratégie qui peut être exprimée par les éléments [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md) et [Type](type-element-net-native.md) diffère de la stratégie qui peut être exprimée pour des membres spécifiques (par les éléments [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), et [Event](event-element-net-native.md)).

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Spécification d'une stratégie pour des assemblys, des espaces de noms et des types

Les éléments [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md) et [Type](type-element-net-native.md) prennent en charge les types de stratégie suivants :

- `Activate`. Contrôle l'accès aux constructeurs, pour permettre l'activation d'instances au moment de l'exécution.

- `Browse`. Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.

- `Dynamic`. Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.

- `Serialize`. Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation des instances de types par des bibliothèques tierces comme le sérialiseur JSON Newtonsoft.

- `DataContractSerializer`. Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.

- `DataContractJsonSerializer`. Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.

- `XmlSerializer`. Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.

- `MarshalObject`. Contrôle la stratégie de marshaling des types référence vers WinRT et COM.

- `MarshalDelegate`. Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.

- `MarshalStructure` . Stratégie de contrôles pour le marshaling de structures en code natif.

Les paramètres associés à ces types de stratégie sont les suivants :

- `All`. Activer la stratégie pour tous les types et membres que la chaîne d'outils ne supprime pas.

- `Auto`. Utiliser le comportement par défaut. (Ne pas spécifier une stratégie équivaut à définir cette stratégie sur `Auto` , sauf si elle est substituée, par exemple par un élément parent.)

- `Excluded`. Désactiver la stratégie pour l'élément de programme.

- `Public`. Activer la stratégie pour les types ou membres publics, sauf si la chaîne d'outils détermine que le membre n'est pas nécessaire et donc le supprime. (Dans ce dernier cas, vous devez utiliser `Required Public` pour vous assurer que le membre est conservé et dispose de fonctionnalités de réflexion.)

- `PublicAndInternal`. Activer la stratégie pour les types ou membres publics et internes si la chaîne d'outils ne les supprime pas.

- `Required Public`. Obliger la chaîne d'outils à conserver les membres et types publics, qu'ils soient utilisés ou non, et à activer la stratégie pour eux.

- `Required PublicAndInternal`. Obliger la chaîne d'outils à conserver les types et membres publics et internes, qu'ils soient utilisés ou non, et à activer la stratégie pour eux.

- `Required All`. Obliger la chaîne d'outils à conserver tous les membres et types, qu'ils soient utilisés ou non, et à activer la stratégie pour eux.

Par exemple, le fichier de directives runtime suivant définit la stratégie pour tous les types et membres de l'assembly DataClasses.dll. Il autorise la réflexion pour la sérialisation de toutes les propriétés publiques, la consultation de tous les types et membres de type, l'activation pour tous les types (en raison de l'attribut `Dynamic`) et la réflexion pour tous les membres et types publics.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"
                Browse="All" Activate="PublicAndInternal"
                Dynamic="Public"  />
   </Application>
   <Library Name="UtilityLibrary">
     <!-- Child elements go here -->
   </Library>
</Directives>
```

### <a name="specifying-policy-for-members"></a>Spécification d'une stratégie pour les membres

Les éléments [Property](property-element-net-native.md) et [Field](field-element-net-native.md) prennent en charge les types de stratégie suivants :

- `Browse` : contrôle la demande d'informations sur le membre concerné, mais ne permet pas l'accès au moment de l'exécution.

- `Dynamic` : contrôle l'accès au moment de l'exécution à tous les membres de type, y compris aux constructeurs, méthodes, champs, propriétés et événements, pour permettre une programmation dynamique. Contrôle également les requêtes d'informations sur le type conteneur.

- `Serialize` : contrôle l'accès au moment de l'exécution au membre pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft. Cette stratégie peut être appliquée à des constructeurs, des champs et des propriétés.

Les éléments [Method](method-element-net-native.md) et [Event](event-element-net-native.md) prennent en charge les types de stratégie suivants :

- `Browse` : contrôle la demande d'informations sur le membre concerné, mais ne permet pas l'accès au moment de l'exécution.

- `Dynamic` : contrôle l'accès au moment de l'exécution à tous les membres de type, y compris aux constructeurs, méthodes, champs, propriétés et événements, pour permettre une programmation dynamique. Contrôle également les requêtes d'informations sur le type conteneur.

 Les paramètres associés à ces types de stratégie sont les suivants :

- `Auto` : utiliser le comportement par défaut. (Ne pas spécifier une stratégie équivaut à définir cette stratégie sur `Auto`, sauf si quelque chose la substitue.)

- `Excluded` : ne jamais inclure de métadonnées pour le membre.

- `Included` : activer la stratégie si le type de parent est présent dans la sortie.

- `Required` : obliger la chaîne d'outils à conserver le membre concerné même s'il semble inutilisé et à activer la stratégie pour lui.

## <a name="runtime-directives-file-semantics"></a>Sémantique du fichier de directives runtime

La stratégie peut être définie simultanément pour les éléments de niveau supérieur et de niveau inférieur. Par exemple, la stratégie peut être définie pour un assembly, ainsi que pour certains des types contenus dans cet assembly. Si un élément particulier de niveau inférieur n'est pas représenté, il hérite la stratégie de son parent. Par exemple, si un élément `Assembly` est présent, mais que des éléments `Type` sont absents, la stratégie spécifiée dans l'élément `Assembly` s'applique à chaque type dans l'assembly. Plusieurs éléments peuvent aussi appliquer la stratégie au même élément de programme. Par exemple, des éléments [Assembly](assembly-element-net-native.md) distincts peuvent définir le même élément de stratégie pour le même assembly différemment. Les sections suivantes expliquent comment la stratégie pour un type particulier est résolue dans ces cas.

Un élément [Type](type-element-net-native.md) ou [Method](method-element-net-native.md) d’une méthode ou type générique applique sa stratégie à toutes les instanciations qui n’ont pas leur propre stratégie. Par exemple, un élément `Type` qui spécifie une stratégie pour <xref:System.Collections.Generic.List%601> s'applique à toutes les instances construites de ce type générique, sauf s'il est substitué pour un type générique construit particulier (comme `List<Int32>`) par un élément `TypeInstantiation`. Dans le cas contraire, les éléments définissent la stratégie pour l'élément de programme nommé.

Quand un élément est ambigu, le moteur recherche des correspondances, et s'il trouve une correspondance exacte, il l'utilise. La présence de plusieurs correspondances entraîne un avertissement ou une erreur.

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>Si deux directives appliquent la stratégie au même élément de programme

Si deux éléments dans des fichiers de directives runtime différents essaient de définir sur des valeurs différentes le même type de stratégie pour le même élément de programme (par exemple, un assembly ou un type), le conflit est résolu comme suit :

1. Si l'élément `Excluded` est présent, il a la priorité.

2. `Required` est prioritaire sur `Required`Not Required{3}.

3. `All` est prioritaire sur `PublicAndInternal`, lui-même prioritaire sur `Public`.

4. Tout paramètre explicite est prioritaire sur `Auto`.

Par exemple, si un projet inclut les deux fichiers de directives runtime suivants, la stratégie de sérialisation pour DataClasses.dll est définie sur `Required Public` et `All`. Dans ce cas, la stratégie de sérialisation est résolue en tant que `Required All`.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"/>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="All" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

Toutefois, si deux directives dans un même fichier de directives runtime essaient de définir le même type de stratégie pour le même élément de programme, l'outil de définition de schéma XML affiche un message d'erreur.

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a>Si des éléments enfants et parents appliquent le même type de stratégie

Les éléments enfants se substituent à leurs éléments parents, y compris au paramètre `Excluded`. La substitution est la principale raison de la spécification du paramètre `Auto`.

Dans l'exemple suivant, le paramètre de stratégie de sérialisation pour tous les éléments de `DataClasses` qui ne se trouvent pas dans `DataClasses.ViewModels` serait `Required Public` et tout ce qui se trouve à la fois dans `DataClasses` et `DataClasses.ViewModels` aurait pour paramètre `All`.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a>Si des génériques ouverts et des éléments instanciés appliquent le même type de stratégie

Dans l'exemple suivant, `Dictionary<int,int>` ne se voit attribuer la stratégie `Browse` que si le moteur a une autre raison de lui attribuer la stratégie `Browse` (qui serait sinon le comportement par défaut) ; toute autre instanciation de <xref:System.Collections.Generic.Dictionary%602> permet la consultation de tous ses membres.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
      <Namespace Name="DataClasses.Generics" />
      <Type Name="Dictionary" Browse="All" />
      <TypeInstantiation Name="Dictionary"
                         Arguments="System.Int32,System.Int32" Browse="Auto" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="how-policy-is-inferred"></a>Mode de déduction de la stratégie

Chaque type de stratégie possède un ensemble spécifique de règles qui déterminent la façon dont la présence de ce type de stratégie affecte les autres constructions.

#### <a name="the-effect-of-browse-policy"></a>Effet de la stratégie Browse

L'application de la stratégie `Browse` à un type implique les modifications de stratégie suivantes :

- Le type de base du type est marqué avec la stratégie `Browse`.

- Si le type est un générique instancié, la version non instanciée du type est marquée avec la stratégie `Browse`.

- Si le type est un délégué, la méthode `Invoke` sur le type est marquée avec la stratégie `Dynamic`.

- Chaque interface du type est marquée avec la stratégie `Browse`.

- Le type de chaque attribut appliqué au type est marqué avec la stratégie `Browse`.

- Si le type est générique, chaque type de contrainte est marqué avec la stratégie `Browse`.

- Si le type est générique, les types sur lesquels il est instancié sont marqués avec la stratégie `Browse`.

L'application de la stratégie `Browse` à une méthode implique les modifications de stratégie suivantes :

- Chaque type de paramètre de la méthode est marqué avec la stratégie `Browse`.

- Le type de retour de la méthode est marqué avec la stratégie `Browse`.

- Le type conteneur de la méthode est marqué avec la stratégie `Browse`.

- Si la méthode est une méthode générique instanciée, la méthode générique non instanciée est marquée avec la stratégie `Browse`.

- Le type de chaque attribut appliqué à la méthode est marqué avec la stratégie `Browse`.

- Si la méthode est générique, chaque type de contrainte est marqué avec la stratégie `Browse`.

- Si la méthode est générique, les types sur lesquels elle est instanciée sont marqués avec la stratégie `Browse`.

L'application de la stratégie `Browse` à un champ implique les modifications de stratégie suivantes :

- Le type de chaque attribut appliqué au champ est marqué avec la stratégie `Browse`.

- Le type du champ est marqué avec la stratégie `Browse`.

- Le type auquel appartient le champ est marqué avec la stratégie `Browse`.

#### <a name="the-effect-of-dynamic-policy"></a>Effet de la stratégie Dynamic

L'application de la stratégie `Dynamic` à un type implique les modifications de stratégie suivantes :

- Le type de base du type est marqué avec la stratégie `Dynamic`.

- Si le type est un générique instancié, la version non instanciée du type est marquée avec la stratégie `Dynamic`.

- Si le type est un type délégué, la méthode `Invoke` sur le type est marqué avec la stratégie `Dynamic`.

- Chaque interface du type est marquée avec la stratégie `Browse`.

- Le type de chaque attribut appliqué au type est marqué avec la stratégie `Browse`.

- Si le type est générique, chaque type de contrainte est marqué avec la stratégie `Browse`.

- Si le type est générique, les types sur lesquels il est instancié sont marqués avec la stratégie `Browse`.

L'application de la stratégie `Dynamic` à une méthode implique les modifications de stratégie suivantes :

- Chaque type de paramètre de la méthode est marqué avec la stratégie `Browse`.

- Le type de retour de la méthode est marqué avec la stratégie `Dynamic`.

- Le type conteneur de la méthode est marqué avec la stratégie `Dynamic`.

- Si la méthode est une méthode générique instanciée, la méthode générique non instanciée est marquée avec la stratégie `Browse`.

- Le type de chaque attribut appliqué à la méthode est marqué avec la stratégie `Browse`.

- Si la méthode est générique, chaque type de contrainte est marqué avec la stratégie `Browse`.

- Si la méthode est générique, les types sur lesquels elle est instanciée sont marqués avec la stratégie `Browse`.

- La méthode peut être appelée par `MethodInfo.Invoke`, et la création de délégué par <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType> devient possible.

L'application de la stratégie `Dynamic` à un champ implique les modifications de stratégie suivantes :

- Le type de chaque attribut appliqué au champ est marqué avec la stratégie `Browse`.

- Le type du champ est marqué avec la stratégie `Dynamic`.

- Le type auquel appartient le champ est marqué avec la stratégie `Dynamic`.

#### <a name="the-effect-of-activation-policy"></a>Effet de la stratégie Activation

L'application de la stratégie Activation à un type implique les modifications de stratégie suivantes :

- Si le type est un générique instancié, la version non instanciée du type est marquée avec la stratégie `Browse`.

- Si le type est un type délégué, la méthode `Invoke` sur le type est marqué avec la stratégie `Dynamic`.

- Les constructeurs du type sont marqués avec la stratégie `Activation`.

L'application de la stratégie `Activation` à une méthode implique la modification de stratégie suivante :

- Le constructeur peut être appelé par les méthodes <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> et <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>. Pour les méthodes, la stratégie `Activation` affecte uniquement les constructeurs.

L'application de la stratégie `Activation` à un champ n'a aucun effet.

#### <a name="the-effect-of-serialize-policy"></a>Effet de la stratégie Serialize

La stratégie `Serialize` permet l'utilisation de sérialiseurs courants basés sur la réflexion. Toutefois, comme les modèles d'accès à la réflexion exacts des sérialiseurs non-Microsoft ne sont pas connus de Microsoft, cette stratégie peut manquer d'efficacité.

L'application de la stratégie `Serialize` à un type implique les modifications de stratégie suivantes :

- Le type de base du type est marqué avec la stratégie `Serialize`.

- Si le type est un générique instancié, la version non instanciée du type est marquée avec la stratégie `Browse`.

- Si le type est un type délégué, la méthode `Invoke` sur le type est marqué avec la stratégie `Dynamic`.

- Si le type est une énumération, un tableau du type est marqué avec la stratégie `Serialize`.

- Si le type implémente <xref:System.Collections.Generic.IEnumerable%601>, `T` est marqué avec la stratégie `Serialize`.

- Si le type est <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601> ou <xref:System.Collections.Generic.IReadOnlyList%601>, `T[]` et <xref:System.Collections.Generic.List%601> sont marqués avec la stratégie `Serialize`, mais aucun membre du type d'interface n'est marqué avec la stratégie `Serialize`.

- Si le type est <xref:System.Collections.Generic.List%601>, aucun de ses membres n'est marqué avec la stratégie `Serialize`.

- Si le type est <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> est marqué avec la stratégie `Serialize`, mais aucun de ses membres n'est marqué avec la stratégie `Serialize`.

- Si le type est <xref:System.Collections.Generic.Dictionary%602>, aucun de ses membres n'est marqué avec la stratégie `Serialize`.

- Si le type implémente <xref:System.Collections.Generic.IDictionary%602>, `TKey` et `TValue` sont marqués avec la stratégie `Serialize`.

- Chaque constructeur, chaque accesseur de propriété et chaque champ sont marqués avec la stratégie `Serialize`.

L'application de la stratégie `Serialize` à une méthode implique les modifications de stratégie suivantes :

- Le type conteneur est marqué avec la stratégie `Serialize`.

- Le type de retour de la méthode est marqué avec la stratégie `Serialize`.

L'application de la stratégie `Serialize` à un champ implique les modifications de stratégie suivantes :

- Le type conteneur est marqué avec la stratégie `Serialize`.

- Le type du champ est marqué avec la stratégie `Serialize`.

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a>Effet des stratégies XmlSerializer, DataContractSerializer et DataContractJsonSerializer

Contrairement à la stratégie de `Serialize`, qui est destinée aux sérialiseurs basés sur la réflexion, les stratégies <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sont utilisées pour activer un ensemble de sérialiseurs connus de la chaîne d’outils .NET Native. Ces sérialiseurs ne sont pas implémentés à l'aide de la réflexion, mais le jeu de types qui peuvent être sérialisés au moment de l'exécution est déterminé de la même manière que les types pouvant faire l'objet d'une réflexion.

Appliquer une de ces stratégies à un type permet de sérialiser celui-ci avec le sérialiseur correspondant. En outre, tous les types que le moteur de sérialisation peut déterminer de manière statique comme nécessitant une sérialisation sont également sérialisables.

Ces stratégies n'ont aucun effet sur les méthodes ou champs.

Pour plus d’informations, consultez la section « Différences entre les sérialiseurs » dans [Migration de votre application du Windows Store vers .NET Native](migrating-your-windows-store-app-to-net-native.md).

## <a name="see-also"></a>Voir aussi

- [Éléments de directive runtime](runtime-directive-elements.md)
- [Réflexion et .NET Native](reflection-and-net-native.md)
