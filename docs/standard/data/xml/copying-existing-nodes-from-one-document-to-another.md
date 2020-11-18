---
title: Copie de nœuds existants d'un document à un autre
ms.date: 03/30/2017
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
ms.openlocfilehash: f4d58fa5aafdd48feff1a768ab0463ac09315476
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829607"
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>Copie de nœuds existants d'un document à un autre
La méthode **ImportNode** est le mécanisme par lequel un nœud ou un sous-arbre de nœuds entier est copié d'un **XmlDocument** à un autre. Le nœud retourné par l'appel est une copie du nœud issu du document source, y compris sur le plan des valeurs d'attribut, du nom du nœud, du type de nœud et de tous les attributs associés à l'espace de noms tels que le préfixe, le nom local et l'URI (Uniform Resource Identifier) d'espace de noms. Le document source n'est pas modifié. À l'issue de l'importation du nœud, il vous reste encore à l'ajouter à l'arborescence à l'aide d'une des méthodes d'insertion de nœuds.  
  
 Dès que le nœud a été joint à son nouveau document, ce dernier en prend possession. En effet, chaque nœud, lors de sa création, possède un document propriétaire, même si les nœuds sont créés dans des fragments de document distincts. Il s’agit d’une exigence imposée par le DOM (Document Object Model) XML, qui est appliquée par le design de création de factory à la classe **XmlDocument**. Par exemple, **CreateElement** constitue la seule solution pour créer de nouveaux nœuds.  
  
 En fonction du type de nœud que présente le nœud importé et de la valeur du paramètre *deep*, d'autres informations sont éventuellement copiées. Cette méthode tente de refléter le comportement attendu si un fragment de code source HTML ou XML était copié d'un document à un autre, en tenant compte du fait que, dans le cas d'un document XML, les deux documents peuvent posséder des définitions de type de document (DTD) différentes.  
  
 Le tableau suivant décrit le comportement spécifique pour chaque type of nœud pouvant être importé.  
  
|Type de nœud|Paramètre *deep* avec la valeur true|Paramètre *deep* avec la valeur false|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|<xref:System.Xml.XmlAttribute.Specified%2A> a la valeur **true** sur XmlAttribute. Les descendants du **XmlAttribute** source sont importés de façon récursive et les nœuds résultants sont assemblés à nouveau pour former le sous-arbre correspondant.|Le paramètre *deep* ne s'applique pas aux nœuds **XmlAttribute**, parce qu'ils emportent toujours avec eux leurs nœuds enfants lorsqu'ils sont importés.|  
|XmlCDataSection|Copie le nœud avec ses données.|Copie le nœud avec ses données.|  
|XmlComment|Copie le nœud avec ses données.|Copie le nœud avec ses données.|  
|XmlDocumentFragment|Les descendants du nœud source sont importés de manière récursive et les nœuds obtenus sont réassemblés pour former le sous-arbre correspondant.|Un **XmlDocumentFragment** vide est créé.|  
|XmlDocumentType|Copie le nœud avec ses données.*|Copie le nœud avec ses données.*|  
|XmlElement|Les descendants de l'élément source sont importés de façon récursive et les nœuds résultants sont assemblés à nouveau pour former le sous-arbre correspondant. **Remarque :** les attributs par défaut ne sont pas copiés. Si le document destinataire de l'importation définit des attributs par défaut pour ce nom d'élément, ces attributs sont assignés.|Les nœuds d'attribut spécifiés de l'élément source sont importés et les nœuds **XmlAttribute** générés sont joints au nouvel élément. Les nœuds descendants ne sont pas copiés. **Remarque :** les attributs par défaut ne sont pas copiés. Si le document destinataire de l'importation définit des attributs par défaut pour ce nom d'élément, ces attributs sont assignés.|  
|XmlEntityReference|Étant donné que les documents source et de destination peuvent comporter des définitions différentes des entités, cette méthode ne copie que le nœud **XmlEntityReference**. Le texte de remplacement n'est pas inclus. Si l'entité est définie dans le document de destination, sa valeur est assignée.|Étant donné que les documents source et de destination peuvent comporter des définitions différentes des entités, cette méthode ne copie que le nœud **XmlEntityReference**. Le texte de remplacement n'est pas inclus. Si l'entité est définie dans le document de destination, sa valeur est assignée.|  
|XmlProcessingInstruction|Copie la cible et la valeur de données à partir du nœud importé.|Copie la cible et la valeur de données à partir du nœud importé.|  
|XmlText|Copie le nœud avec ses données.|Copie le nœud avec ses données.|  
|XmlSignificantWhitespace|Copie le nœud avec ses données.|Copie le nœud avec ses données.|  
|XmlWhitespace|Copie le nœud avec ses données.|Copie le nœud avec ses données.|  
|XmlDeclaration|Copie la cible et la valeur de données à partir du nœud importé.|Copie la cible et la valeur de données à partir du nœud importé.|  
|Tous les autres types de nœuds|Ces types de nœuds ne peuvent pas être importés.|Ces types de nœuds ne peuvent pas être importés.|  
  
> [!NOTE]
> Bien que les nœuds DocumentType puissent être importés, un document ne peut avoir qu'un seul DocumentType. Par conséquent, dès que vous avez importé le type de document, vous devez vous assurer, avant de l’insérer dans l’arborescence, que le document est dépourvu de type de document. Pour plus d’informations sur la suppression de nœuds, consultez [Suppression de nœuds, de contenu et de valeurs d'un document XML](removing-nodes-content-and-values-from-an-xml-document.md).  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
