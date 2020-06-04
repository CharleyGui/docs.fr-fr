---
title: Liste des types de données
ms.date: 07/20/2015
helpviewer_keywords:
- Boolean data type [Visual Basic], supported types in Visual Basic
- storage [Visual Basic], order of storage
- data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], supported types in Visual Basic
- notation [Visual Basic], scientific
- memory requirements, data types
- user-defined data types [Visual Basic], Visual Basic
- Date data type [Visual Basic], Visual Basic
- Visual Basic, data types
- storage [Visual Basic], allocation
- Integer data type [Visual Basic], Visual Basic data types
- storage [Visual Basic], space
- Variant data types [Visual Basic], supported types in Visual Basic
- Char data type [Visual Basic], Visual Basic data types
- intrinsic data types [Visual Basic]
- memory consumption [Visual Basic], data types
- single-precision numbers
- data types [Visual Basic], order of storage
- Long data type [Visual Basic], supported types in Visual Basic
- String data type [Visual Basic], Visual Basic data types
- storage order, data types
- StructLayoutAttribute class, Visual Basic data type storage
- scientific notation
- Double data type [Visual Basic], Visual Basic data types
- Byte data type [Visual Basic], Visual Basic data types
- Object data type [Visual Basic], supported types in Visual Basic
- data types [Visual Basic], storage allocation
- double-precision numbers
- data types [Visual Basic], summary
- dates [Visual Basic], data types
- strings [Visual Basic], data types
- memory consumption
- storage order, controlling in Visual Basic
- data types [Visual Basic], memory requirements
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
ms.openlocfilehash: 5eb52ef937a677c0b7498d058b5a39a375351ddc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415620"
---
# <a name="data-type-summary-visual-basic"></a>Liste des types de données (Visual Basic)

Le tableau suivant présente les types de données Visual Basic, leurs types de common language runtime de prise en charge, leur allocation de stockage nominal et leurs plages de valeurs.  
  
|Type de Visual Basic|Structure du type Common Language Runtime|Allocation de stockage nominal|Plage de valeurs|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Booléen](boolean-data-type.md)|<xref:System.Boolean>|Dépend de la plateforme d’implémentation|`True` ou `False`|  
|[Poids](byte-data-type.md)|<xref:System.Byte>|1 octet|0 à 255 (non signé)|  
|[Char](char-data-type.md) (caractère unique)|<xref:System.Char>|2 octets|0 à 65535 (non signé)|  
|[Date](date-data-type.md)|<xref:System.DateTime>|8 octets|0:00:00 (minuit) le 1er janvier 0001 à 11:59:59 PM le 31 décembre 9999|  
|[Décimal](decimal-data-type.md)|<xref:System.Decimal>|16 octets|0 à +/-79 228 162 514 264 337 593 543 950 335 (+/-7.9...E + 28) <sup>†</sup> sans virgule décimale ; 0 à +/-7,9228162514264337593543950335 avec 28 décimales à droite de la virgule ;<br /><br /> le plus petit nombre différent de zéro est +/-0,0000000000000000000000000001 (+/-1E-28) <sup>†</sup>|  
|[Double](double-data-type.md) (virgule flottante double précision)|<xref:System.Double>|8 octets|-1.79769313486231570 e + 308 à-4.94065645841246544 E-324 <sup>†</sup> pour les valeurs négatives ;<br /><br /> 4.94065645841246544 e-324 à 1.79769313486231570 E + 308 <sup>†</sup> pour les valeurs positives|  
|[Integer](integer-data-type.md)|<xref:System.Int32>|4 octets|-2 147 483 648 à 2 147 483 647 (signé)|  
|[Long](long-data-type.md) (entier long)|<xref:System.Int64>|8 octets|-9223372036854775808 à 9 223 372 036 854 775 807 (9.2... E + 18 <sup>†</sup>) (signé)|  
|[Object](object-data-type.md)|<xref:System.Object>type|4 octets sur une plateforme 32 bits<br /><br /> 8 octets sur une plateforme 64 bits|Tout type peut être stocké dans une variable de type`Object`|  
|[SByte](sbyte-data-type.md)|<xref:System.SByte>|1 octet|-128 à 127 (signé)|  
|[Short](short-data-type.md) (entier Short)|<xref:System.Int16>|2 octets|-32 768 à 32 767 (signé)|  
|[Single](single-data-type.md) (virgule flottante simple précision)|<xref:System.Single>|4 octets|-3.4028235 e + 38 à-1.401298 E-45 <sup>†</sup> pour les valeurs négatives ;<br /><br /> 1.401298 e-45 à 3.4028235 E + 38 <sup>†</sup> pour les valeurs positives|  
|[String](string-data-type.md) (longueur variable)|<xref:System.String>type|Dépend de la plateforme d’implémentation|0 à environ 2 milliards caractères Unicode|  
|[UInteger](uinteger-data-type.md)|<xref:System.UInt32>|4 octets|0 à 4 294 967 295 (non signé)|  
|[Correspondante](ulong-data-type.md)|<xref:System.UInt64>|8 octets|0 à 18446744073709551615 (1,8... E + 19 <sup>†</sup>) (non signé)|  
|[Défini par l’utilisateur](user-defined-data-type.md) (structure)|(hérite de <xref:System.ValueType> )|Dépend de la plateforme d’implémentation|Chaque membre de la structure a une plage déterminée par son type de données et indépendamment des plages des autres membres.|  
|[UShort](ushort-data-type.md)|<xref:System.UInt16>|2 octets|0 à 65 535 (non signé)|  
  
 <sup>†</sup> En *notation scientifique*, « E » fait référence à une puissance de 10. Ainsi 3.56 E + 2 signifie 3,56 x 10<sup>2</sup> ou 356, et 3.56 e-2 signifie 3,56/10<sup>2</sup> ou 0,0356.  
  
> [!NOTE]
> Pour les chaînes contenant du texte, utilisez la <xref:Microsoft.VisualBasic.Strings.StrConv%2A> fonction pour convertir un format de texte en un autre.  
  
 En plus de spécifier un type de données dans une instruction de déclaration, vous pouvez forcer le type de données de certains éléments de programmation à l’aide d’un caractère de type. Consultez [caractères de type](../../programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Consommation de mémoire  

 Lorsque vous déclarez un type de données élémentaire, il n’est pas possible de supposer que sa consommation de mémoire est identique à son allocation de stockage nominal. Les considérations suivantes sont à prendre en compte :  
  
- **Affectation de stockage.** La common language runtime peut attribuer le stockage en fonction des caractéristiques actuelles de la plateforme sur laquelle votre application s’exécute. Si la mémoire est presque saturée, elle peut empaqueter vos éléments déclarés aussi étroitement que possible. Dans d’autres cas, il peut aligner leurs adresses mémoire sur des limites matérielles naturelles pour optimiser les performances.  
  
- **Largeur de la plateforme.** L’affectation de stockage sur une plateforme 64 bits diffère de l’affectation sur une plateforme 32 bits.  
  
### <a name="composite-data-types"></a>Types de données composites  

 Les mêmes considérations s’appliquent à chaque membre d’un type de données composite, tel qu’une structure ou un tableau. Vous ne pouvez pas vous appuyer simplement sur l’ajout des allocations de stockage nominal des membres du type. En outre, il existe d’autres considérations, telles que les suivantes :  
  
- **Surcharge.** Certains types composites ont des besoins en mémoire supplémentaires. Par exemple, un tableau utilise de la mémoire supplémentaire pour le tableau lui-même et pour chaque dimension. Sur une plateforme 32 bits, cette surcharge est actuellement de 12 octets et de 8 octets pour chaque dimension. Sur une plateforme 64 bits, cette exigence est doublée.  
  
- **Disposition du stockage.** Vous ne pouvez pas supposer en toute sécurité que l’ordre de stockage en mémoire est identique à celui de votre ordre de déclaration. Vous ne pouvez même pas faire d’hypothèses sur l’alignement des octets, par exemple une limite de 2 ou 4 octets. Si vous définissez une classe ou une structure et que vous devez contrôler la disposition de stockage de ses membres, vous pouvez appliquer l' <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut à la classe ou à la structure.  
  
### <a name="object-overhead"></a>Surcharge des objets  

 Une `Object` référence à un type de données élémentaire ou composite utilise 4 octets en plus des données contenues dans le type de données.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Strings.StrConv%2A>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [Liste des conversions](../keywords/conversion-summary.md)
- [Caractères de type](../../programming-guide/language-features/data-types/type-characters.md)
- [Utilisation efficace des types de données](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
