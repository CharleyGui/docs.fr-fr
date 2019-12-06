---
title: Espaces de noms XAML pour les services XAML .NET Framework
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 11bf5d112c64fb0b942decf7635f02b90a98bdeb
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837166"
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>Espaces de noms XAML pour les services XAML .NET Framework
Un espace de noms XAML est un concept qui s’étend sur la définition d’un espace de noms XML. À l’instar d’un espace de noms XML, vous pouvez définir un espace de noms XAML à l’aide d’un attribut `xmlns` dans le balisage. Les espaces de noms XAML sont également représentés dans le flux de nœud XAML et d’autres API de services XAML. Cette rubrique définit le concept d’espace de noms XAML et décrit comment les espaces de noms XAML peuvent être définis et sont utilisés par les contextes de schéma XAML et d’autres aspects de .NET Framework les services XAML.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Espace de noms XML et espace de noms XAML  
 Un espace de noms XAML est un espace de noms XML spécialisé, tout comme XAML est une forme spécialisée de XML et utilise le formulaire XML de base pour son balisage. Dans le balisage, vous déclarez un espace de noms XAML et son mappage via un attribut `xmlns` appliqué à un élément. La déclaration `xmlns` peut être faite au même élément que celui dans lequel l’espace de noms XAML est déclaré. Une déclaration d’espace de noms XAML transmise à un élément est valide pour cet élément, tous les attributs de cet élément et tous les enfants de cet élément. Les attributs peuvent utiliser un espace de noms XAML qui n’est pas le même que l’élément qui contient l’attribut, tant que le nom de l’attribut lui-même fait référence au préfixe dans le cadre de son nom d’attribut dans le balisage.  
  
 La distinction entre un espace de noms XAML et un espace de noms XML est qu’un espace de noms XML peut être utilisé pour référencer un schéma ou qu’il peut être utilisé pour différencier des entités. Pour XAML, les types et les membres utilisés dans XAML doivent finalement être résolus en types de stockage, et les concepts de schéma XML ne s’appliquent pas bien à cette fonctionnalité. L’espace de noms XAML contient des informations que le contexte de schéma XAML doit avoir pour effectuer ce mappage de type.  
  
## <a name="xaml-namespace-components"></a>Composants d’espace de noms XAML  
 La définition de l’espace de noms XAML comporte deux composants : un préfixe et un identificateur. Chacun de ces composants est présent lorsqu’un espace de noms XAML est déclaré dans le balisage, ou défini dans le système de type XAML.  
  
 Le préfixe peut être n’importe quelle chaîne autorisée par les [espaces de noms W3C dans la spécification XML 1,0](https://www.w3.org/TR/REC-xml-names/) . Par Convention, les préfixes sont généralement des chaînes très courtes, car le préfixe est répété plusieurs fois dans un fichier de balisage classique. Certains espaces de noms XAML qui sont destinés à être utilisés dans plusieurs implémentations XAML utilisent des préfixes conventionnels particuliers. Par exemple, l’espace de noms XAML du langage XAML est généralement mappé à l’aide du préfixe `x`. Vous pouvez définir un espace de noms XAML par défaut, où le préfixe n’est pas fourni dans la définition, mais qui est représenté sous la forme d’une chaîne vide si elle est définie ou interrogée par by.NET Framework XAML Services API. En règle générale, l’espace de noms XAML par défaut est délibérément choisi afin de promouvoir une quantité agrandie de balisage à omission de préfixe par une technologie d’implémentation XAML, ainsi que ses scénarios et vocabulaires.  
  
 L’identificateur peut être n’importe quelle chaîne autorisée par les [espaces de noms W3C dans la spécification XML 1,0](https://www.w3.org/TR/REC-xml-names/). Par Convention, les identificateurs pour les espaces de noms XML ou XAML sont souvent fournis sous forme d’URI, généralement sous la forme d’un URI absolu de protocole. Souvent, les informations de version qui définissent un vocabulaire XAML particulier sont implicites dans le cadre de la chaîne de chemin d’accès. Les espaces de noms XAML ajoutent une convention d’identificateur supplémentaire au-delà de la Convention d’URI XML. Pour les espaces de noms XAML, l’identificateur communique les informations nécessaires à un contexte de schéma XAML pour résoudre les types spécifiés en tant qu’éléments sous cet espace de noms XAML, ou pour résoudre les attributs en membres.  
  
 Pour permettre la communication d’informations à un contexte de schéma XAML, l’identificateur d’un espace de noms XAML peut encore être sous forme d’URI. Toutefois, dans ce cas, l’URI est également déclaré comme identificateur correspondant dans un assembly particulier ou une liste d’assemblys. Cela s’effectue dans les assemblys en attribuant l’assembly avec <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Cette méthode d’identification de l’espace de noms XAML et de prise en charge d’un comportement de résolution de type CLR dans l’assembly avec attributs est prise en charge par le contexte de schéma XAML par défaut dans .NET Framework les services XAML. Plus généralement, cette Convention peut être utilisée dans les cas où le contexte de schéma XAML intègre le CLR ou s’il est basé sur le contexte de schéma XAML par défaut, ce qui est nécessaire pour lire les attributs CLR à partir des assemblys CLR.  
  
 Les espaces de noms XAML peuvent également être identifiés par une convention qui communique un espace de noms CLR et un assembly de définition de type. Cette Convention est utilisée dans les cas où aucune attribution de <xref:System.Windows.Markup.XmlnsDefinitionAttribute> n’existe dans les assemblys qui contiennent des types. Cette Convention est potentiellement plus complexe que la Convention d’URI, et elle présente également le risque d’ambiguïté et de duplication, car il existe plusieurs façons de faire référence à un assembly.  
  
 La forme la plus simple d’un identificateur qui utilise l’espace de noms CLR et la Convention d’assembly est la suivante :  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` et `; assembly=` sont des composants littéraux de la syntaxe.  
  
 *clrnsName* est le nom de chaîne qui identifie un espace de noms CLR. Ce nom de chaîne comprend tous les caractères point internes (.) qui fournissent des indications sur l’espace de noms CLR et sa relation aux autres espaces de noms CLR.  
  
 *NomCourtAssembly* est le nom de chaîne d’un assembly qui définit les types qui sont utiles en XAML. Les types accessibles par le biais de l’espace de noms XAML déclaré sont censés être définis par l’assembly et être déclarés spécifiquement dans l’espace de noms CLR spécifié par *clrnsName*. Ce nom de chaîne correspond généralement aux informations signalées par <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Une définition plus complète de la Convention d’assembly et de l’espace de noms CLR est la suivante :  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyName*  
  
 *AssemblyName* représente toute chaîne autorisée comme entrée de <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>. Cette chaîne peut inclure des informations sur la culture, la clé publique ou la version (les définitions de ces concepts sont définies dans la rubrique de référence pour <xref:System.Reflection.Assembly>). Le format et la preuve COFF (utilisés par d’autres surcharges de <xref:System.Reflection.Assembly.Load%2A>) ne sont pas pertinents pour le chargement d’un assembly XAML. toutes les informations de chargement doivent être présentées sous la forme d’une chaîne.  
  
 La spécification d’une clé publique pour l’assembly est une technique utile pour la sécurité XAML, ou pour la suppression de l’ambiguïté possible qui peut exister si les assemblys sont chargés par nom simple ou préexistants dans un cache ou un domaine d’application. Pour plus d’informations, consultez [Considérations sur la sécurité XAML](xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Déclarations d’espace de noms XAML dans l’API des services XAML  
 Dans l’API des services XAML, une déclaration d’espace de noms XAML est représentée par un objet <xref:System.Xaml.NamespaceDeclaration>. Si vous déclarez un espace de noms XAML dans le code, vous appelez le constructeur <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29>. Les paramètres `ns` et `prefix` sont spécifiés en tant que chaînes, et l’entrée à fournir pour ces paramètres correspond à la définition de l’identificateur d’espace de noms XAML et au préfixe d’espace de noms XAML comme indiqué précédemment dans cette rubrique.  
  
 Si vous examinez les informations d’espace de noms XAML dans le cadre d’un flux de nœud XAML ou par le biais d’un autre accès au système de type XAML, <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> signale l’identificateur d’espace de noms XAML et <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> signale le préfixe d’espace de noms XAML.  
  
 Dans un flux de nœud XAML, les informations d’espace de noms XAML peuvent apparaître sous la forme d’un nœud XAML qui précède l’entité à laquelle il s’applique. Cela comprend les cas où les informations d’espace de noms XAML précèdent le `StartObject` de l’élément racine XAML. Pour plus d'informations, consultez [Understanding XAML Node Stream Structures and Concepts](understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Pour de nombreux scénarios qui utilisent .NET Framework API de services XAML, au moins une déclaration d’espace de noms XAML est supposée exister, et la déclaration doit contenir ou référencer des informations requises par un contexte de schéma XAML. Les espaces de noms XAML doivent spécifier les assemblys à charger ou aider à résoudre des types spécifiques dans les espaces de noms et les assemblys déjà chargés ou connus par le contexte de schéma XAML.  
  
 Pour générer un flux de nœud XAML, les informations de type XAML doivent être disponibles via le contexte de schéma XAML. Les informations de type XAML ne peuvent pas être déterminées sans déterminer d’abord l’espace de noms XAML approprié pour chaque nœud à créer. À ce stade, aucune instance de type n’est encore créée, mais le contexte de schéma XAML peut avoir besoin de rechercher des informations à partir de l’assembly de définition et du type de stockage. Par exemple, pour traiter le balisage `<Party><PartyFavor/></Party>`, le contexte de schéma XAML doit être en mesure de déterminer le nom et le type de l' `ContentProperty` de `Party`, et doit donc connaître les informations d’espace de noms XAML pour `Party` et `PartyFavor`. Dans le cas du contexte de schéma XAML par défaut, la réflexion statique signale une grande partie des informations de système de type XAML nécessaires pour générer des nœuds de type XAML dans le flux de nœud.  
  
 Pour générer un graphique d’objet à partir d’un flux de nœud XAML, les déclarations d’espaces de noms XAML doivent exister pour chaque préfixe XAML utilisé dans le balisage d’origine et enregistrées dans le flux de nœud XAML. À ce stade, les instances sont en cours de création et un véritable comportement de mappage de type se produit.  
  
 Si vous devez préremplir les informations d’espace de noms XAML, dans les cas où l’espace de noms XAML que vous prévoyez d’utiliser pour le contexte de schéma XAML n’est pas défini dans le balisage, une technique que vous pouvez utiliser consiste à déclarer des déclarations d’espaces de noms XML dans la <xref:System.Xml.XmlParserContext> pour une <xref:System.Xml.XmlReader>. Utilisez ensuite ce <xref:System.Xml.XmlReader> comme entrée pour un constructeur de lecteur XAML, ou <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 Les deux autres API qui sont pertinentes pour la gestion des espaces de noms XAML dans .NET Framework services XAML sont les attributs <xref:System.Windows.Markup.XmlnsDefinitionAttribute> et <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Ces attributs s’appliquent aux assemblys. <xref:System.Windows.Markup.XmlnsDefinitionAttribute> est utilisé par un contexte de schéma XAML pour interpréter toute déclaration d’espace de noms XAML qui comprend un URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute> est utilisé par les outils qui émettent du code XAML afin qu’un espace de noms XAML particulier puisse être sérialisé avec un préfixe prévisible. Pour plus d’informations, consultez [attributs CLR XAML pour les bibliothèques et les types personnalisés](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fonctionnement des concepts et structures du flux de nœud XAML](understanding-xaml-node-stream-structures-and-concepts.md)
