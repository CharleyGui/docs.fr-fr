---
title: Définition de types personnalisés pour une utilisation avec les services XAML .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: 7437add6795c1bb7f8a59807ebfc51dc2d0f987f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972020"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>Définition de types personnalisés pour une utilisation avec les services XAML .NET Framework
Quand vous définissez des types personnalisés qui sont des objets métier ou des types qui n’ont pas de dépendance sur des frameworks spécifiques, il existe certaines meilleures pratiques pour XAML que vous pouvez suivre. Si vous suivez ces pratiques, .NET Framework les services XAML et ses lecteurs et writers XAML peuvent découvrir les caractéristiques XAML de votre type et lui attribuer la représentation appropriée dans un flux de nœud XAML à l’aide du système de type XAML. Cette rubrique décrit les meilleures pratiques pour les définitions de type, les définitions de membres et l’attribution CLR de types ou de membres.  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Modèles de constructeur et définitions de type pour XAML  
 Pour être instancié en tant qu’élément objet en XAML, une classe personnalisée doit remplir les conditions suivantes :  
  
- La classe personnalisée doit être publique et doit exposer un constructeur public sans paramètre. (Consultez la section suivante pour des remarques concernant les structures.)  
  
- La classe personnalisée ne doit pas être une classe imbriquée. Le « point » supplémentaire dans le chemin de nom complet rend la Division de l’espace de noms de classe ambiguë et interfère avec d’autres fonctionnalités XAML telles que les propriétés jointes.  
  
 Si un objet peut être instancié en tant qu’élément objet, l’objet créé peut remplir la forme d’élément de propriété de toutes les propriétés qui prennent l’objet comme type sous-jacent.  
  
 Vous pouvez toujours fournir des valeurs d’objet pour les types qui ne répondent pas à ces critères, si vous activez un convertisseur de valeur. Pour plus d’informations, consultez [convertisseurs de type et extensions de balisage pour XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
### <a name="structures"></a>Structures  
 Les structures peuvent toujours être construites en XAML, par définition CLR. Cela est dû au fait qu’un compilateur CLR crée implicitement un constructeur sans paramètre pour une structure. Ce constructeur initialise toutes les valeurs de propriété à leurs valeurs par défaut.  
  
 Dans certains cas, le comportement de construction par défaut d’une structure n’est pas souhaitable. Cela peut être dû au fait que la structure est conçue pour remplir les valeurs et la fonction conceptuellement comme une Union. En tant qu’Union, les valeurs contenues peuvent avoir des interprétations mutuellement exclusives et, par conséquent, aucune de ses propriétés ne peut être définie. <xref:System.Windows.GridLength>est un exemple de cette structure dans le vocabulaire WPF. De telles structures doivent implémenter un convertisseur de type afin que les valeurs puissent être exprimées sous forme d’attribut, en utilisant des conventions de chaîne qui créent les différentes interprétations ou modes des valeurs de structure. La structure doit également exposer un comportement similaire pour la construction de code via un constructeur sans paramètre.  
  
### <a name="interfaces"></a>Interfaces  
 Les interfaces peuvent être utilisées comme types sous-jacents de membres. Le système de type XAML vérifie la liste assignable et s’attend à ce que l’objet fourni comme valeur puisse être assigné à l’interface. Il n’existe aucun concept de présentation de l’interface en tant que type XAML, à condition qu’un type assignable pertinent prenne en charge les spécifications de construction XAML.  
  
### <a name="factory-methods"></a>Méthodes de fabrique  
 Les méthodes de fabrique sont une fonctionnalité XAML 2009. Ils modifient le principe XAML selon lequel les objets doivent avoir des constructeurs sans paramètre. Les méthodes de fabrique ne sont pas documentées dans cette rubrique. Consultez [directive x :FactoryMethod](x-factorymethod-directive.md).  
  
## <a name="enumerations"></a>Énumérations  
 Les énumérations ont un comportement de conversion de type natif XAML. Les noms de constantes d’énumération spécifiés dans XAML sont résolus par rapport au type d’énumération sous-jacent et retournent la valeur d’énumération dans un writer d’objet XAML.  
  
 XAML prend en charge une utilisation de style indicateurs pour les énumérations avec <xref:System.FlagsAttribute> appliqué. Pour plus d’informations, consultez [syntaxe XAML en détail](../wpf/advanced/xaml-syntax-in-detail.md). (La[syntaxe XAML est écrite en détail](../wpf/advanced/xaml-syntax-in-detail.md) pour l’audience WPF, mais la plupart des informations contenues dans cette rubrique s’appliquent à du code XAML qui n’est pas spécifique à une infrastructure d’implémentation particulière.)  
  
## <a name="member-definitions"></a>Définitions de membres  
 Les types peuvent définir des membres pour l’utilisation de XAML. Il est possible pour les types qui définissent des membres qui sont utilisables en XAML même si ce type spécifique n’est pas utilisable en XAML. Cela est possible en raison de l’héritage CLR. Tant qu’un type qui hérite du membre prend en charge l’utilisation de XAML en tant que type, et que le membre prend en charge l’utilisation de XAML pour son type sous-jacent ou possède une syntaxe XAML native disponible, ce membre est utilisable en XAML.  
  
### <a name="properties"></a>Propriétés  
 Si vous définissez des propriétés en tant que propriété CLR publique à l’aide d’un `get` CLR standard et de modèles d’accesseur `set` et de mots de frappe appropriés au langage, le système de type XAML peut signaler la propriété en tant que membre avec les informations appropriées fournies pour les propriétés de <xref:System.Xaml.XamlMember>, telles que <xref:System.Xaml.XamlMember.IsReadPublic%2A> et <xref:System.Xaml.XamlMember.IsWritePublic%2A>.  
  
 Des propriétés spécifiques peuvent activer une syntaxe de texte en appliquant <xref:System.ComponentModel.TypeConverterAttribute>. Pour plus d’informations, consultez [convertisseurs de type et extensions de balisage pour XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 En l’absence d’une syntaxe de texte ou d’une conversion XAML native et en l’absence d’une autre indirection, telle qu’une utilisation d’extension de balisage, le type d’une propriété (<xref:System.Xaml.XamlMember.TargetType%2A> dans le système de type XAML) doit être en mesure de retourner une instance à un writer d’objet XAML en traitant le type cible comme un type CLR.  
  
 Si vous utilisez XAML 2009, l' [extension de balisage x :Reference](x-reference-markup-extension.md) peut être utilisée pour fournir des valeurs si les considérations précédentes ne sont pas remplies ; Toutefois, il s’agit d’un problème d’utilisation plus qu’un problème de définition de type.  
  
### <a name="events"></a>événements  
 Si vous définissez des événements comme un événement CLR public, le système de type XAML peut signaler l’événement en tant que membre avec <xref:System.Xaml.XamlMember.IsEvent%2A> comme `true`. La connexion des gestionnaires d’événements n’est pas comprise dans l’étendue des .NET Framework les fonctionnalités des services XAML. elle est conservée dans des infrastructures et des implémentations spécifiques.  
  
### <a name="methods"></a>Méthodes  
 Le code inline pour les méthodes n’est pas une fonctionnalité XAML par défaut. Dans la plupart des cas, vous ne référencez pas directement des membres de méthode à partir de XAML, et le rôle des méthodes en XAML est uniquement de fournir la prise en charge de modèles XAML spécifiques. [la directive x :FactoryMethod](x-factorymethod-directive.md) est une exception.  
  
### <a name="fields"></a>Champs  
 Les instructions de conception du CLR découragent les champs non statiques. Pour les champs statiques, vous pouvez accéder aux valeurs de champ statiques uniquement par le biais de l' [extension de balisage x :static](x-static-markup-extension.md); dans ce cas, vous n’avez rien de spécial dans la définition du CLR pour exposer un champ pour les utilisations de [x :static](x-static-markup-extension.md) .  
  
## <a name="attachable-members"></a>Membres pouvant être attachés  
 Les membres pouvant être attachés sont exposés au code XAML via un modèle de méthode d’accesseur sur un type de définition. Le type de définition lui-même n’a pas besoin d’être utilisable en XAML en tant qu’objet. En fait, un modèle courant consiste à déclarer une classe de service dont le rôle est de posséder le membre pouvant être attaché et d’implémenter les comportements associés, mais qui n’a aucune autre fonction telle qu’une représentation d’interface utilisateur. Dans les sections suivantes, l’espace réservé *PropertyName* représente le nom de votre membre pouvant être attaché. Ce nom doit être valide dans la [grammaire XamlName](xamlname-grammar.md).  
  
 Méfiez-vous des collisions de noms entre ces modèles et d’autres méthodes d’un type. Si un membre existant correspond à l’un des modèles, il peut être interprété comme une voie d’utilisation de membre pouvant être attaché par un processeur XAML, même si ce n’est pas votre intention.  
  
#### <a name="the-getpropertyname-accessor"></a>Accesseur GetPropertyName  
 La signature pour l’accesseur `Get`*NomPropriété* doit être :  
  
 `public static object Get` *NomPropriété* `(object`  `target` `)`  
  
- L’objet `target` peut être défini comme un type plus spécifique dans votre implémentation. Vous pouvez l’utiliser pour étendre l’utilisation de votre membre pouvant être attaché ; les utilisations en dehors de votre portée prévue lèvent des exceptions de cast non valides qui sont ensuite représentées par une erreur d’analyse XAML. Le nom du paramètre `target` n’est pas obligatoire, mais il est nommé `target` par Convention dans la plupart des implémentations.  
  
- La valeur de retour peut être spécifiée comme un type plus spécifique dans votre implémentation.  
  
 Pour prendre en charge une syntaxe de texte <xref:System.ComponentModel.TypeConverter> activée pour l’utilisation des attributs du membre pouvant être attaché, appliquez <xref:System.ComponentModel.TypeConverterAttribute> à l’accesseur `Get`*PropertyName* . L’application de la `get` au lieu du `set` peut paraître non intuitive ; Toutefois, cette Convention peut prendre en charge le concept de membres pouvant être attachés en lecture seule qui sont sérialisables, ce qui est utile dans les scénarios de concepteur.  
  
#### <a name="the-setpropertyname-accessor"></a>Accesseur SetPropertyName  
 La signature de l’accesseur Set*PropertyName* doit être :  
  
 `public static void Set` *NomPropriété* `(object`  `target` `, object`  `value` `)`  
  
- L’objet `target` peut être spécifié en tant que type plus spécifique dans votre implémentation, avec la même logique et les mêmes conséquences que celles décrites dans la section précédente.  
  
- L’objet `value` peut être défini comme un type plus spécifique dans votre implémentation.  
  
 N’oubliez pas que la valeur de cette méthode est l’entrée provenant de l’utilisation de XAML, généralement sous la forme d’un attribut. À partir du formulaire d’attribut, il doit y avoir une prise en charge de convertisseur de valeurs pour une syntaxe de texte, et vous Attributez sur l’accesseur `Get`*PropertyName* .  
  
### <a name="attachable-member-stores"></a>Magasins de membres pouvant être attachés  
 Les méthodes d’accesseur ne sont généralement pas suffisantes pour fournir un moyen de placer des valeurs de membre pouvant être attachées dans un graphique d’objet, ou pour récupérer des valeurs à partir du graphique d’objet et les sérialiser correctement. Pour fournir cette fonctionnalité, les objets `target` dans les signatures d’accesseur précédentes doivent pouvoir stocker des valeurs. Le mécanisme de stockage doit être cohérent avec le principe de membre pouvant être attaché que le membre peut être attaché aux cibles où le membre pouvant être attaché ne figure pas dans la liste des membres. Les services XAML .NET Framework fournissent une technique d’implémentation pour les magasins de membres pouvant être attachés via les API <xref:System.Xaml.IAttachedPropertyStore> et <xref:System.Xaml.AttachablePropertyServices>. <xref:System.Xaml.IAttachedPropertyStore> est utilisé par les writers XAML pour découvrir l’implémentation du magasin et doit être implémenté sur le type qui est le `target` des accesseurs. Les API <xref:System.Xaml.AttachablePropertyServices> statiques sont utilisées dans le corps des accesseurs et font référence au membre pouvant être attaché par son <xref:System.Xaml.AttachableMemberIdentifier>.  
  
## <a name="xaml-related-clr-attributes"></a>Attributs CLR liés à XAML  
 L’attribution correcte de vos types, membres et assemblys est importante pour signaler les informations du système de type XAML à .NET Framework les services XAML. Cela est pertinent si vous souhaitez que vos types soient utilisés avec les systèmes XAML qui sont directement basés sur .NET Framework les services XAML, les lecteurs XAML et les writers XAML, ou si vous définissez ou utilisez un Framework utilisant XAML basé sur ces lecteurs et writers XAML.  
  
 Pour obtenir la liste de chaque attribut XAML qui est pertinent pour la prise en charge XAML de vos types personnalisés, consultez [attributs CLR XAML pour les bibliothèques et les types personnalisés](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="usage"></a>Utilisation  
 L’utilisation de types personnalisés requiert que l’auteur du balisage doive mapper un préfixe pour l’assembly et l’espace de noms CLR qui contiennent le type personnalisé. Cette procédure n’est pas décrite dans cette rubrique.  
  
## <a name="access-level"></a>Niveau d’accès  
 XAML fournit un moyen de charger et d’instancier des types qui ont un niveau d’accès `internal`. Cette fonctionnalité est fournie afin que le code utilisateur puisse définir ses propres types, puis instancier ces classes à partir du balisage qui fait également partie de la même portée de code utilisateur.  
  
 Un exemple de WPF est à chaque fois que le code utilisateur définit une <xref:System.Windows.Controls.UserControl> qui est destinée à refactoriser un comportement d’interface utilisateur, mais pas dans le cadre d’un mécanisme d’extension possible qui peut être implicite en déclarant la classe de prise en charge avec `public` niveau d’accès. Une telle <xref:System.Windows.Controls.UserControl> peut être déclarée avec l’accès `internal` si le code de stockage est compilé dans le même assembly que celui à partir duquel il est référencé en tant que type XAML.  
  
 Pour une application qui charge le code XAML en confiance totale et utilise <xref:System.Xaml.XamlObjectWriter>, le chargement de classes avec `internal` niveau d’accès est toujours activé.  
  
 Pour une application qui charge le code XAML en confiance partielle, vous pouvez contrôler les caractéristiques du niveau d’accès à l’aide de l’API <xref:System.Xaml.Permissions.XamlAccessLevel>. En outre, les mécanismes de report (tels que le système de modèles WPF) doivent être en mesure de propager toutes les autorisations de niveau d’accès et de les conserver pour les évaluations de l’heure d’exécution. Cela est géré en interne en passant les informations de <xref:System.Xaml.Permissions.XamlAccessLevel>.  
  
### <a name="wpf-implementation"></a>Implémentation WPF  
 Le XAML WPF utilise un modèle d’accès de confiance partielle où si BAML est chargé en mode de confiance partielle, l’accès est limité à <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> pour l’assembly qui est la source BAML. Pour report, WPF utilise <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> comme mécanisme de transmission des informations de niveau d’accès.  
  
 Dans la terminologie XAML WPF, un *type interne* est un type défini par le même assembly qui comprend également le XAML de référencement. Un tel type peut être mappé par le biais d’un espace de noms XAML qui omet délibérément la partie assembly = d’un mappage, par exemple, `xmlns:local="clr-namespace:WPFApplication1"`.  Si BAML fait référence à un type interne et que ce type a `internal` niveau d’accès, cela génère une classe `GeneratedInternalTypeHelper` pour l’assembly. Si vous souhaitez éviter `GeneratedInternalTypeHelper`, vous devez utiliser le niveau d’accès `public` ou vous devez factoriser la classe pertinente dans un assembly distinct et rendre cet assembly dépendant.  
  
## <a name="see-also"></a>Voir aussi

- [Attributs CLR XAML pour les bibliothèques et types personnalisés](xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [Services XAML](index.md)
