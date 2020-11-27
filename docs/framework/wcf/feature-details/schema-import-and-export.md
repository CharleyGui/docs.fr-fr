---
title: Importation et exportation de schémas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
ms.openlocfilehash: 52a9e1bf4c9442bd42beb55b133a185c4a42148d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288563"
---
# <a name="schema-import-and-export"></a>Importation et exportation de schémas

Windows Communication Foundation (WCF) comprend un nouveau moteur de sérialisation, le <xref:System.Runtime.Serialization.DataContractSerializer> . Le `DataContractSerializer` traduit entre les objets .NET Framework et XML (dans les deux sens). En plus du sérialiseur lui-même, WCF comprend des mécanismes d’importation et d’exportation de schémas associés. Le *schéma* est une description formelle, précise et explicite de la forme du code XML que le sérialiseur produit ou auquel le désérialiseur peut accéder. WCF utilise le langage XSD (XML Schema Definition Language) World Wide Web Consortium (W3C) comme représentation de schéma, qui est largement interopérable avec de nombreuses plateformes tierces.  
  
 Le composant d’importation de schéma, <xref:System.Runtime.Serialization.XsdDataContractImporter> , prend un document de schéma XSD et génère des classes .NET Framework (normalement les classes de contrat de données) de telle sorte que les formulaires sérialisés correspondent au schéma donné.  
  
 Par exemple, le fragment de schéma suivant :  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 génère le type suivant (légèrement simplifié pour permettre une meilleure compréhension).  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 Notez que le type généré suit plusieurs pratiques recommandées relatives aux contrats de données (disponibles dans [meilleures pratiques :](../best-practices-data-contract-versioning.md)contrôle de version des contrats de données) :  
  
- Ce type implémente l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject>. Pour plus d’informations, consultez [Contrats de données compatibles avec des versions ultérieures](forward-compatible-data-contracts.md).  
  
- Les membres de données sont implémentés sous forme de propriétés publiques qui encapsulent des champs privés.  
  
- La classe est une classe partielle et des éléments peuvent y être ajoutés sans modifier le code généré.  
  
 L'exportateur <xref:System.Runtime.Serialization.XsdDataContractExporter> vous permet d'effectuer l'opération inverse, c'est-à-dire de prendre des types pouvant être sérialisés à l'aide de `DataContractSerializer`, puis de générer un document de schéma XSD.  
  
## <a name="fidelity-is-not-guaranteed"></a>Fidélité non garantie  

 Lors de la conversion, puis reconversion des schémas ou types, la stricte fidélité des informations converties n'est pas garantie. (Un aller- *retour* signifie que vous importez un schéma pour créer un ensemble de classes et que vous exportez le résultat pour créer à nouveau un schéma.) Le même schéma ne peut pas être retourné. Effectuer à nouveau le processus dans le sens inverse ne garantit pas en effet la fidélité aux informations d'origine. (Exportez un type pour générer son schéma, puis réimportez le type. Il est improbable que le même type soit retourné.)  
  
## <a name="supported-types"></a>Types pris en charge  

 Le modèle de contrat de données prend uniquement en charge un sous-ensemble limité de schémas WC3. Tout schéma ne se conformant pas à ce sous-ensemble provoquera la levée d'une exception lors de l'importation. Par exemple, il n'est pas possible d'indiquer qu'un membre de données d'un contrat de données doit être sérialisé sous forme d'attribut XML. Les schémas nécessitant l'utilisation d'attributs XML ne sont donc pas pris en charge et provoqueront la levée d'exceptions lors de l'importation, le contrat de données ne pouvant être généré à l'aide des attributs XML appropriés.  
  
 Par exemple, il est impossible d'importer le fragment de schéma suivant à l'aide des paramètres d'importation par défaut.  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 Pour plus d’informations, consultez [Référence du schéma de contrat de données](data-contract-schema-reference.md). Lorsqu'un schéma ne se conforme pas aux règles des contrats de données, utilisez un autre moteur de sérialisation. Le moteur de sérialisation <xref:System.Xml.Serialization.XmlSerializer> utilise, par exemple, son propre mécanisme d'importation de schéma. De plus, il existe un mode spécial d'importation dans lequel la plage du schéma pris en charge est développée. Pour plus d’informations, consultez la section relative à la génération <xref:System.Xml.Serialization.IXmlSerializable> de types dans [importation de schéma pour générer des classes](importing-schema-to-generate-classes.md).  
  
 `XsdDataContractExporter`Prend en charge tous les types de .NET Framework qui peuvent être sérialisés avec le `DataContractSerializer` . Pour plus d’informations, consultez [types pris en charge par le sérialiseur de contrat de données](types-supported-by-the-data-contract-serializer.md). Remarque : le schéma généré à l'aide de `XsdDataContractExporter` contient en principe des données utilisables par l'importateur `XsdDataContractImporter`, sauf si <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> est utilisé afin de personnaliser ce schéma).  
  
 Pour plus d’informations sur l’utilisation de <xref:System.Runtime.Serialization.XsdDataContractImporter> , consultez [importation de schéma pour générer des classes](importing-schema-to-generate-classes.md).  
  
 Pour plus d’informations sur l’utilisation de <xref:System.Runtime.Serialization.XsdDataContractExporter> , consultez [exportation de schémas à partir de classes](exporting-schemas-from-classes.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Importation du schéma pour générer des classes](importing-schema-to-generate-classes.md)
- [Exportation de schémas à partir de classes](exporting-schemas-from-classes.md)
