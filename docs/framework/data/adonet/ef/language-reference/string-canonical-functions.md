---
title: Fonctions de chaînes canoniques
ms.date: 03/30/2017
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
ms.openlocfilehash: 9013b8bd8505442666dd0688eaf2586959a61b70
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249089"
---
# <a name="string-canonical-functions"></a>Fonctions de chaînes canoniques
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] inclut des fonctions canoniques de chaîne.  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant présente les fonctions canoniques [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de chaîne.  
  
|Fonction|Description|  
|--------------|-----------------|  
|`Concat(string1, string2)`|Retourne une chaîne qui contient `string2` ajouté à `string1`.<br /><br /> **Arguments**<br /><br /> `string1`: Chaîne à laquelle `string2` est ajouté.<br /><br /> `string2`: Chaîne à `string1`laquelle est ajouté.<br /><br /> **Valeur de retour**<br /><br /> `String` Une erreur se produit si la longueur de la chaîne de valeur de retour est supérieure à la longueur maximale autorisée.<br /><br /> **Exemple**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains(string, target)`|Retourne `true` si `target` est contenu dans `string`.<br /><br /> **Arguments**<br /><br /> `string`: Chaîne dans laquelle la recherche est effectuée.<br /><br /> `target`: Chaîne cible recherchée.<br /><br /> **Valeur de retour**<br /><br /> `true` si `target` est contenu dans `string` ; sinon, `false`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith(string, target)`|Retourne `true` si `target` se termine par `string`.<br /><br /> **Arguments**<br /><br /> `string`: Chaîne dans laquelle la recherche est effectuée.<br /><br /> `target`: Chaîne cible recherchée à la fin de `string`.<br /><br /> **Valeur de retour**<br /><br /> `True` si `string` se termine par `target` ; sinon, `false`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')` **Remarque :**  Si vous utilisez le fournisseur de données SQL Server, cette fonction retourne `false` si la chaîne est stockée dans une colonne de chaîne de `target` longueur fixe et est une constante. Dans ce cas, la chaîne entière est recherchée, y compris les éventuels espaces de remplissage de fin. Une solution de contournement possible consiste à découper les données dans la chaîne de longueur fixe, comme dans l'exemple suivant : `EndsWith(TRIM(string), target)`|  
|`IndexOf(target, string)`|Retourne la position de la chaîne `target` dans `string` ou 0 si elle est introuvable. Retourne 1 pour indiquer le début de `string`. La numérotation de l'index commence à 1.<br /><br /> **Arguments**<br /><br /> `target`: Chaîne recherchée.<br /><br /> `string`: Chaîne dans laquelle la recherche est effectuée.<br /><br /> **Valeur de retour**<br /><br /> Élément `Int32`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left(string, length)`|Retourne les `length` premiers caractères du côté gauche de `string`. Si la longueur de `string` est inférieure à `length`, la chaîne est retournée dans son intégralité.<br /><br /> **Arguments**<br /><br /> `string`: `String`<br /><br /> `length`: ,, Ou`Byte`. `Int16` `Int32` `Int64` `length` ne peut pas être inférieur à zéro.<br /><br /> **Valeur de retour**<br /><br /> `String`<br /><br /> **Exemple**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length(string)`|Retourne la longueur (`Int32`), en caractères, de la chaîne.<br /><br /> **Arguments**<br /><br /> `string`: `String`<br /><br /> **Valeur de retour**<br /><br /> Élément `Int32`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(string)`|Retourne `string` sans espace blanc de début.<br /><br /> **Arguments**<br /><br /> `String`<br /><br /> **Valeur de retour**<br /><br /> `String`<br /><br /> **Exemple**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace(string1, string2, string3)`|Retourne `string1`, avec toutes les occurrences de `string2` remplacées par `string3`.<br /><br /> **Arguments**<br /><br /> `String`<br /><br /> **Valeur de retour**<br /><br /> `String`<br /><br /> **Exemple**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse(string)`|Retourne `string` avec l'ordre des caractères inversé.<br /><br /> **Arguments**<br /><br /> `String`<br /><br /> **Valeur de retour**<br /><br /> `String`<br /><br /> **Exemple**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right(string, length)`|Retourne les derniers `length` caractères `string`de. Si la longueur de `string` est inférieure à `length`, la chaîne est retournée dans son intégralité.<br /><br /> **Arguments**<br /><br /> `string`: `String`<br /><br /> `length`: ,, Ou`Byte`. `Int16` `Int32` `Int64` `length` ne peut pas être inférieur à zéro.<br /><br /> **Valeur de retour**<br /><br /> `String`<br /><br /> **Exemple**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(string)`|Retourne `string` sans espace blanc de fin.<br /><br /> **Arguments**<br /><br /> `String`<br /><br /> **Valeur de retour**<br /><br /> `String`|  
|`Substring(string, start, length)`|Retourne la sous-chaîne de la chaîne qui commence à la position `start` et compte `length` caractères. La valeur 1 pour start indique le premier caractère de la chaîne. La numérotation de l'index commence à 1.<br /><br /> **Arguments**<br /><br /> `string`: `String`<br /><br /> `start`: `Int16` ,`Int32`Et .`Byte` `Int64` `start` ne peut pas être inférieur à un.<br /><br /> `length`: `Int16` ,`Int32`Et .`Byte` `Int64` `length` ne peut pas être inférieur à zéro.<br /><br /> **Valeur de retour**<br /><br /> `String`<br /><br /> **Exemple**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith(string, target)`|Retourne `true` si `string` commence par `target`.<br /><br /> **Arguments**<br /><br /> `string`: Chaîne dans laquelle la recherche est effectuée.<br /><br /> `target`: Chaîne cible recherchée au début de `string`.<br /><br /> **Valeur de retour**<br /><br /> `True` si `string` commence par `target` ; sinon, `false`.<br /><br /> **Exemple**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(string)`|Retourne `string` avec tous les caractères majuscules convertis en minuscules.<br /><br /> **Arguments**<br /><br /> `String`<br /><br /> **Valeur de retour**<br /><br /> `String`<br /><br /> **Exemple**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(string)`|Retourne `string` avec tous les caractères minuscules convertis en majuscules.<br /><br /> **Arguments**<br /><br /> `String`<br /><br /> **Valeur de retour**<br /><br /> `String`<br /><br /> **Exemple**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(string)`|Retourne `string` sans espace blanc de début et de fin.<br /><br /> **Arguments**<br /><br /> `String`<br /><br /> **Valeur de retour**<br /><br /> `String`<br /><br /> **Exemple**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 Ces fonctions retournent `null` si une entrée de valeur `null` est fournie.  
  
 Des fonctionnalités équivalentes sont disponibles dans le fournisseur managé Client Microsoft SQL. Pour plus d’informations, consultez [SqlClient pour les fonctions de Entity Framework](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions canoniques](canonical-functions.md)
