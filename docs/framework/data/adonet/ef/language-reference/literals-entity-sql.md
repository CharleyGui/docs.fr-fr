---
title: Littéraux (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
ms.openlocfilehash: 4402f4c6ee38432a0f606e39dd4a18639076ce04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161774"
---
# <a name="literals-entity-sql"></a>Littéraux (Entity SQL)

Cette rubrique décrit la prise en charge des littéraux dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="null"></a>Null  

 Le littéral Null est utilisé pour représenter la valeur Null d'un type quel qu'il soit. Un littéral Null est compatible avec n'importe quel type.  
  
 Des valeurs Null typées peuvent être créées par cast sur un littéral Null. Pour plus d’informations, consultez [Cast](cast-entity-sql.md).  
  
 Pour connaître les règles permettant d’utiliser des littéraux NULL flottants libres, consultez [littéraux NULL et inférence de type](null-literals-and-type-inference-entity-sql.md).  
  
## <a name="boolean"></a>Boolean  

 Les littéraux booléens sont représentés par les mots clés `true` et `false`.  
  
## <a name="integer"></a>Entier  

 Les littéraux entiers (integer) peuvent être de type <xref:System.Int32> ou <xref:System.Int64>. Un littéral <xref:System.Int32> est une série de caractères numériques. Un littéral <xref:System.Int64> est une série de caractères numériques suivie d'un L majuscule.  
  
## <a name="decimal"></a>Decimal  

 Un nombre à virgule fixe (decimal) est une série de caractères numériques entrecoupée d'une virgule (,) et suivie d'un M majuscule.  
  
## <a name="float-double"></a>Float, Double  

 Un nombre à virgule flottante double précision est une série de caractères numériques entrecoupée d'une virgule (,) et suivie d'un exposant. Un nombre à virgule flottante simple précision (ou float) est une syntaxe de nombre à virgule flottante double précision suivie d'un f minuscule.  
  
## <a name="string"></a>String  

 Une chaîne (string) est une série de caractères figurant entre guillemets. Les guillemets peuvent être soit simples (`'`) tous les deux, soit doubles (") tous les deux. Les littéraux de chaîne de caractères peuvent être au format Unicode ou non. Pour déclarer un littéral de chaîne de caractères comme étant au format Unicode, faites-le précéder d'un N majuscule. Par défaut, les littéraux de chaîne de caractères ne sont pas au format Unicode. Aucun espace ne doit figurer entre le N et la charge utile du littéral de chaîne, et le N doit être majuscule.  
  
```sql  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a>DateTime  

 Un littéral de date/heure (datetime) est indépendant des paramètres régionaux. Il est composé d'une partie date et d'une partie heure. Ces deux parties sont obligatoires et il n'existe pas de valeur par défaut.  
  
 La partie date doit avoir le format : `YYYY` - `MM` - `DD` , où `YYYY` est une valeur d’année à quatre chiffres comprise entre 0001 et 9999, `MM` est le mois compris entre 1 et 12 et `DD` est la valeur du jour qui est valide pour le mois donné `MM` .  
  
 La partie heure doit avoir le format : `HH`:`MM`[:`SS`[.fffffff]], où `HH` est la valeur des heures comprise entre 0 et 23 inclus, `MM` est la valeur des minutes comprise entre 0 et 59 inclus, `SS` est la valeur des secondes comprise entre 0 et 59 inclus, et fffffff est la valeur des fractions de seconde comprise entre 0 et 9999999. Toutes les plages de valeurs sont inclusives. Les fractions de secondes sont facultatives. Les secondes sont facultatives à moins que les fractions de secondes soient spécifiées ; auquel cas, les secondes sont requises. Lorsque les secondes ou les fractions de secondes ne sont pas spécifiées, la valeur par défaut zéro est utilisée.  
  
 Le symbole DATETIME et la charge utile du littéral peuvent être séparés d'autant d'espaces que nécessaire, mais pas de nouvelles lignes.  
  
```sql  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a>Temps  

 Un littéral d'heure (time) est indépendant des paramètres régionaux. Il n'est composé que d'une partie heure. La partie heure est obligatoire et n'est assortie d'aucune valeur par défaut. Elle doit respecter le format HH:MM[:SS[.fffffff]], où HH est la valeur des heures comprise entre 0 et 23 inclus, MM est la valeur des minutes comprise entre 0 et 59 inclus, SS est la valeur des secondes comprise entre 0 et 59 inclus, et fffffff est la valeur des fractions de seconde comprise entre 0 et 9999999 inclus. Toutes les plages de valeurs sont inclusives. Les fractions de secondes sont facultatives. Les secondes sont facultatives à moins que les fractions de secondes soient spécifiées ; auquel cas, les secondes sont requises. Lorsque les secondes ou les fractions de secondes ne sont pas spécifiées, la valeur par défaut zéro est utilisée.  
  
 Le symbole TIME et la charge utile du littéral peuvent être séparés d'autant d'espaces que nécessaire, mais pas de nouvelles lignes.  
  
```sql  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a>DateTimeOffset  

 Un littéral datetimeoffset est indépendant des paramètres régionaux. Il est composé d'une partie date, d'une partie heure et d'une partie décalage. Toutes ces parties sont obligatoires et il n'existe pas de valeur par défaut. La partie date doit respecter le format YYYY-MM-DD, où YYYY est une année à quatre chiffres comprise entre 0001 et 9999, MM est une valeur comprise entre 1 et 12 qui représente le mois et DD est la valeur du jour valide pour le mois donné. La partir heure doit respecter le format HH:MM[:SS[.fffffff]], où HH est la valeur des heures comprise entre 0 et 23 inclus, MM est la valeur des minutes comprise entre 0 et 59 inclus, SS est la valeur des secondes comprise entre 0 et 59 inclus, et fffffff est la valeur des fractions de seconde comprise entre 0 et 9999999 inclus. Toutes les plages de valeurs sont inclusives. Les fractions de secondes sont facultatives. Les secondes sont facultatives à moins que les fractions de secondes soient spécifiées ; auquel cas, les secondes sont requises. Lorsque les secondes ou les fractions de secondes ne sont pas spécifiées, la valeur par défaut zéro est utilisée. La partie de décalage doit avoir le format {+&#124;-} HH : MM, où HH et MM ont la même signification que dans la partie heure. Toutefois, la plage du décalage doit être comprise entre -14:00 et +14:00.  
  
 Le symbole DATETIMEOFFSET et la charge utile du littéral peuvent être séparés d'autant d'espaces que nécessaire, mais pas de nouvelles lignes.  
  
```sql  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> Une valeur littérale Entity SQL valide peut se situer hors des plages prises en charge pour CLR ou la source de données. Cela peut donner lieu à une exception.  
  
## <a name="binary"></a>Binary  

 Un littéral de chaîne binaire (binary) est une séquence de chiffres hexadécimaux délimitée par des guillemets simples à la suite du mot clé binary ou du symbole de raccourci `X` ou `x`. Le symbole de raccourci `X` ne respecte pas la casse. Notez que les espaces sont autorisés entre le mot clé `binary` et la valeur de chaîne binaire.  
  
 Les caractères hexadécimaux ne respectent pas la casse. Si le littéral est composé d'un nombre impair de chiffres hexadécimaux, un chiffre zéro hexadécimal lui sera ajouté en préfixe pour permettre son alignement sur le prochain chiffre hexadécimal pair. Il n'existe pas de limite formelle relativement à la taille de la chaîne binaire.  
  
```sql  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a>Guid  

 Un littéral `GUID` représente un identificateur global unique. Il s’agit d’une séquence formée par le mot clé `GUID` suivi de chiffres hexadécimaux sous la forme « format de *registre* : 8-4-4-4-12 » entre guillemets simples. Les chiffres hexadécimaux ne respectent pas la casse.  
  
 Le symbole GUID et la charge utile du littéral peuvent être séparés d'autant d'espaces que nécessaire, mais pas de nouvelles lignes.  
  
```sql  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
