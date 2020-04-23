---
title: XAML Namespaces pour .NET XAML Services
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 2ae57d08fade85c59fea2a54b653a2f775b57415
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071842"
---
# <a name="xaml-namespaces-for-net-xaml-services"></a>XAML Namespaces pour .NET XAML Services
Un espace de nom XAML est un concept qui s’étend sur la définition d’un espace de nom XML. Semblable à un espace de nom XML, vous pouvez `xmlns` définir un espace de nom XAML à l’aide d’un attribut dans la balisage. Les espaces de noms XAML sont également représentés dans le flux de nœuds XAML et d’autres API de XAML Services. Ce sujet définit le concept XAML namespace, et décrit comment les espaces de nom XAML peuvent être définis et sont utilisés par les contextes schémas XAML et d’autres aspects de .NET XAML Services.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>XML Namespace et XAML Namespace  
 Un espace de nom XAML est un espace de nom XML spécialisé, tout comme XAML est une forme spécialisée de XML et utilise le formulaire XML de base pour sa balisage. En balisage, vous déclarez un espace de `xmlns` nom XAML et sa cartographie à travers un attribut appliqué à un élément. La `xmlns` déclaration peut être faite au même élément que l’espace de nom XAML est déclaré dans. Une déclaration XAML namespace faite à un élément est valable pour cet élément, tous les attributs de cet élément, et tous les enfants de cet élément. Les attributs peuvent utiliser un espace de nom XAML qui n’est pas le même que l’élément qui contient l’attribut, tant que le nom d’attribut lui-même fait référence au préfixe dans le cadre de son nom d’attribut dans la balisage.  
  
 La distinction d’un espace de nom XAML par rapport à un espace de nom XML est qu’un espace de nom XML peut être utilisé pour référencer un schéma ou simplement pour différencier les entités. Pour XAML, les types et les membres utilisés dans XAML doivent finalement être résolus aux types de support, et les concepts de schémas XML ne s’appliquent pas bien à cette capacité. L’espace de nom XAML contient des informations que le contexte du schéma XAML doit avoir disponible afin d’effectuer cette cartographie de type.  
  
## <a name="xaml-namespace-components"></a>Composants XAML Namespace  
 La définition XAML namespace comporte deux composants : un préfixe et un identifiant. Chacun de ces composants est présent lorsqu’un espace de nom XAML est déclaré en marge, ou défini dans le système de type XAML.  
  
 Le préfixe peut être n’importe quelle chaîne comme le permet les [namespaces W3C dans XML 1.0 spécification](https://www.w3.org/TR/REC-xml-names/). Par convention, les préfixes sont généralement des cordes courtes, parce que le préfixe est répété plusieurs fois dans un fichier de balisage typique. Certains espaces de noms XAML qui sont destinés à être utilisés dans plusieurs implémentations XAML utilisent des préfixes conventionnels particuliers. Par exemple, l’espace de nom XAML en langue `x`XAML est généralement cartographié à l’aide du préfixe . Vous pouvez définir un espace de nom XAML par défaut, où le préfixe n’est pas donné dans la définition, mais est représenté comme une chaîne vide si défini ou interrogé by.NET’API XAML Services. Typiquement, l’espace de nom XAML par défaut est délibérément choisi afin de promouvoir une quantité maximisée de préfixe-omettant balisage par une technologie de mise en œuvre XAML et ses scénarios et vocabulaires.  
  
 L’identifiant peut être n’importe quelle chaîne comme le permet les [namespaces W3C dans la spécification XML 1.0](https://www.w3.org/TR/REC-xml-names/). Par convention, les identifiants pour les espaces de noms XML ou les espaces de noms XAML sont souvent donnés sous forme d’URI, généralement comme un URI absolu qualifié par protocole. Souvent, l’information de version qui définit un vocabulaire XAML particulier est implicite dans le cadre de la chaîne de chemin. Les espaces de noms XAML ajoutent une convention d’identification supplémentaire au-delà de la convention XML URI. Pour les espaces de noms XAML, l’identifiant communique les informations qui sont nécessaires par un contexte schéma XAML afin de résoudre les types qui sont spécifiés comme éléments en vertu de cet espace de nom XAML, ou de résoudre les attributs aux membres.  
  
 Aux fins de la communication d’informations à un contexte de schéma XAML, l’identifiant d’un espace de nom XAML peut encore être sous forme d’URI. Toutefois, dans ce cas, l’URI est également déclarée identificateur correspondant dans une assemblée ou une liste particulière d’assemblées. Cela se fait dans les assemblées <xref:System.Windows.Markup.XmlnsDefinitionAttribute>en attribuant l’assemblée avec . Cette méthode d’identification de l’espace de nom XAML et de soutien d’un comportement de résolution de type CLR dans l’assemblage attribué est soutenue par le contexte par défaut de schéma XAML dans .NET XAML Services. Plus généralement, cette convention peut être utilisée pour les cas où le contexte du schéma XAML intègre le CLR ou est basé sur le contexte de schéma XAML par défaut, qui est nécessaire pour lire les attributs CLR des assemblages CLR.  
  
 Les espaces de noms XAML peuvent également être identifiés par une convention qui communique un espace de nom CLR et un assemblage de type définissant. Cette convention est utilisée <xref:System.Windows.Markup.XmlnsDefinitionAttribute> dans les cas où il n’existe pas d’attribution dans les assemblées qui contiennent des types. Cette convention est potentiellement plus complexe que la convention de l’URI, et a également le potentiel d’ambiguïté et de duplication, parce qu’il existe de multiples façons de se référer à une assemblée.  
  
 La forme la plus élémentaire d’un identifiant qui utilise l’espace de nom CLR et la convention d’assemblage est la suivante:  
  
 `clr-namespace:clrnsName; assembly=assemblyShortName`
  
 `clr-namespace:`et `; assembly=` sont des composants littérals de la syntaxe.  
  
 *clrnsName* est le nom de chaîne qui identifie un namespace CLR. Ce nom de chaîne inclut tous les caractères de point interne (.) qui fournissent des conseils au sujet de l’espace de nom CLR et sa relation aux autres espaces de nom CLR.
  
 *assemblageShortName* est le nom de chaîne d’un assemblage qui définit les types qui sont utiles dans XAML. Les types à accéder par l’espace de nom XAML déclarés devraient être définis par l’assemblage et être déclarés dans l’espace nom CLR spécifié par *clrnsName*. Ce nom de chaîne est généralement <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>parallèle à l’information telle que rapportée par .  
  
 Une définition plus complète de l’espace de nom CLR et de la convention d’assemblage est la suivante :  
  
 `clr-namespace:clrnsName; assembly=assemblyName`
  
 *assemblyName* représente toute chaîne qui <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> est légale comme une entrée. Cette chaîne peut inclure la culture, la clé publique, ou l’information <xref:System.Reflection.Assembly>de version (définitions de ces concepts sont définies dans le sujet de référence pour ). Le format et les éléments de preuve <xref:System.Reflection.Assembly.Load%2A>du COFF (utilisés par d’autres surcharges) ne sont pas pertinents aux fins de chargement d’assemblage XAML; toutes les informations de charge doivent être présentées comme une chaîne.  
  
 Spécifier une clé publique pour l’assemblage est une technique utile pour la sécurité XAML, ou pour éliminer l’ambiguïté possible qui peut exister si les assemblages sont chargés par un nom simple, ou pré-exister dans un cache ou un domaine d’application. Pour plus d’informations, voir [XAML Security Considerations](security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Déclarations XAML Namespace dans l’API XAML Services  
 Dans l’API XAML Services, une déclaration XAML <xref:System.Xaml.NamespaceDeclaration> namespace est représentée par un objet. Si vous déclarez un espace de nom XAML dans le code, vous appelez le <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> constructeur. Les `ns` `prefix` paramètres et les paramètres sont spécifiés comme des chaînes, et l’entrée à fournir pour ces paramètres correspond à la définition de l’identifiant XAML namespace et XAML namespace préfixe comme prévu précédemment dans ce sujet.  
  
 Si vous examinez les informations XAML namespace dans le cadre d’un flux de <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> nœuds XAML ou <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> par le biais d’un autre accès au système de type XAML, signale l’identifiant XAML namespace, et signale le préfixe XAML namespace.  
  
 Dans un flux de nœuds XAML, les informations XAML namespace peuvent apparaître comme un nœud XAML qui précède l’entité à laquelle il s’applique. Cela comprend les cas où l’information `StartObject` XAML namespace précède l’élément racine XAML. Pour plus d'informations, consultez [Understanding XAML Node Stream Structures and Concepts](understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Pour de nombreux scénarios qui utilisent .NET XAML Services API, au moins une déclaration XAML namespace devrait exister, et la déclaration doit soit contenir ou se référer à des informations qui sont nécessaires par un contexte schéma XAML. Les espaces de noms XAML doivent soit spécifier les assemblages à charger, soit aider à résoudre des types spécifiques dans des espaces nominaux et des assemblages qui sont déjà chargés ou connus par le contexte du schéma XAML.  
  
 Afin de générer un flux de nœuds XAML, des informations de type XAML doivent être disponibles, dans le contexte du schéma XAML. Les informations de type XAML ne peuvent pas être déterminées sans d’abord déterminer l’espace de nom XAML pertinent pour chaque nœud à créer. À ce stade, aucun cas de types n’est encore créé, mais le contexte du schéma XAML peut avoir besoin de rechercher des informations de l’assemblage définissant et le type de soutien. Par exemple, afin de traiter `<Party><PartyFavor/></Party>`le balisage , le contexte schéma XAML `ContentProperty` doit `Party`être en mesure de déterminer le nom `Party` `PartyFavor`et le type de , et doit donc également connaître les informations XAML namespace pour et . Dans le cas du contexte par défaut du schéma XAML, la réflexion statique rapporte une grande partie des informations du système de type XAML qui sont nécessaires pour générer des nœuds de type XAML dans le flux de nœuds.  
  
 Afin de générer un graphique d’objets à partir d’un flux de nœuds XAML, les déclarations de namespace XAML doivent exister pour chaque préfixe XAML utilisé dans le balisage original et enregistré dans le flux de nœuds XAML. À ce stade, des instances sont créées, et un véritable comportement de cartographie de type se produit.  
  
 Si vous avez besoin de prépopuler les informations XAML namespace, dans les cas où l’espace de nom XAML vous avez l’intention du <xref:System.Xml.XmlParserContext> contexte <xref:System.Xml.XmlReader>schéma XAML à utiliser n’est pas défini dans le balisage, une technique que vous pouvez utiliser est de déclarer les déclarations XML namespace dans le pour un . Ensuite, <xref:System.Xml.XmlReader> utilisez-le comme entrée pour un <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>constructeur de lecteurs XAML, ou .  
  
 Deux autres API qui sont pertinents pour la manipulation de l’espace <xref:System.Windows.Markup.XmlnsDefinitionAttribute> de <xref:System.Windows.Markup.XmlnsPrefixAttribute>nom XAML dans .NET XAML Services sont les attributs et . Ces attributs s’appliquent aux assemblages. <xref:System.Windows.Markup.XmlnsDefinitionAttribute>est utilisé par un contexte de schéma XAML pour interpréter toute déclaration de namespace XAML qui comprend un URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute>est utilisé par des outils qui émettent XAML de sorte qu’un espace de nom XAML particulier peut être sérialisé avec un préfixe prévisible. Pour plus d’informations, consultez [les attributs CLR liés à XAML pour les types et bibliothèques personnalisés](clr-attributes-with-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fonctionnement des concepts et structures du flux de nœud XAML](understanding-xaml-node-stream-structures-and-concepts.md)
