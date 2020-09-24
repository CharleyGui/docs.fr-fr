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
# <a name="literals-entity-sql"></a><span data-ttu-id="16643-102">Littéraux (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="16643-102">Literals (Entity SQL)</span></span>

<span data-ttu-id="16643-103">Cette rubrique décrit la prise en charge des littéraux dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16643-103">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="16643-104">Null</span><span class="sxs-lookup"><span data-stu-id="16643-104">Null</span></span>  

 <span data-ttu-id="16643-105">Le littéral Null est utilisé pour représenter la valeur Null d'un type quel qu'il soit.</span><span class="sxs-lookup"><span data-stu-id="16643-105">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="16643-106">Un littéral Null est compatible avec n'importe quel type.</span><span class="sxs-lookup"><span data-stu-id="16643-106">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="16643-107">Des valeurs Null typées peuvent être créées par cast sur un littéral Null.</span><span class="sxs-lookup"><span data-stu-id="16643-107">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="16643-108">Pour plus d’informations, consultez [Cast](cast-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="16643-108">For more information, see [CAST](cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="16643-109">Pour connaître les règles permettant d’utiliser des littéraux NULL flottants libres, consultez [littéraux NULL et inférence de type](null-literals-and-type-inference-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="16643-109">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="16643-110">Boolean</span><span class="sxs-lookup"><span data-stu-id="16643-110">Boolean</span></span>  

 <span data-ttu-id="16643-111">Les littéraux booléens sont représentés par les mots clés `true` et `false`.</span><span class="sxs-lookup"><span data-stu-id="16643-111">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="16643-112">Entier</span><span class="sxs-lookup"><span data-stu-id="16643-112">Integer</span></span>  

 <span data-ttu-id="16643-113">Les littéraux entiers (integer) peuvent être de type <xref:System.Int32> ou <xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="16643-113">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="16643-114">Un littéral <xref:System.Int32> est une série de caractères numériques.</span><span class="sxs-lookup"><span data-stu-id="16643-114">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="16643-115">Un littéral <xref:System.Int64> est une série de caractères numériques suivie d'un L majuscule.</span><span class="sxs-lookup"><span data-stu-id="16643-115">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="16643-116">Decimal</span><span class="sxs-lookup"><span data-stu-id="16643-116">Decimal</span></span>  

 <span data-ttu-id="16643-117">Un nombre à virgule fixe (decimal) est une série de caractères numériques entrecoupée d'une virgule (,) et suivie d'un M majuscule.</span><span class="sxs-lookup"><span data-stu-id="16643-117">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="16643-118">Float, Double</span><span class="sxs-lookup"><span data-stu-id="16643-118">Float, Double</span></span>  

 <span data-ttu-id="16643-119">Un nombre à virgule flottante double précision est une série de caractères numériques entrecoupée d'une virgule (,) et suivie d'un exposant.</span><span class="sxs-lookup"><span data-stu-id="16643-119">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="16643-120">Un nombre à virgule flottante simple précision (ou float) est une syntaxe de nombre à virgule flottante double précision suivie d'un f minuscule.</span><span class="sxs-lookup"><span data-stu-id="16643-120">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="16643-121">String</span><span class="sxs-lookup"><span data-stu-id="16643-121">String</span></span>  

 <span data-ttu-id="16643-122">Une chaîne (string) est une série de caractères figurant entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="16643-122">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="16643-123">Les guillemets peuvent être soit simples (`'`) tous les deux, soit doubles (") tous les deux.</span><span class="sxs-lookup"><span data-stu-id="16643-123">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="16643-124">Les littéraux de chaîne de caractères peuvent être au format Unicode ou non.</span><span class="sxs-lookup"><span data-stu-id="16643-124">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="16643-125">Pour déclarer un littéral de chaîne de caractères comme étant au format Unicode, faites-le précéder d'un N majuscule.</span><span class="sxs-lookup"><span data-stu-id="16643-125">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="16643-126">Par défaut, les littéraux de chaîne de caractères ne sont pas au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="16643-126">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="16643-127">Aucun espace ne doit figurer entre le N et la charge utile du littéral de chaîne, et le N doit être majuscule.</span><span class="sxs-lookup"><span data-stu-id="16643-127">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```sql  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="16643-128">DateTime</span><span class="sxs-lookup"><span data-stu-id="16643-128">DateTime</span></span>  

 <span data-ttu-id="16643-129">Un littéral de date/heure (datetime) est indépendant des paramètres régionaux. Il est composé d'une partie date et d'une partie heure.</span><span class="sxs-lookup"><span data-stu-id="16643-129">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="16643-130">Ces deux parties sont obligatoires et il n'existe pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="16643-130">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="16643-131">La partie date doit avoir le format : `YYYY` - `MM` - `DD` , où `YYYY` est une valeur d’année à quatre chiffres comprise entre 0001 et 9999, `MM` est le mois compris entre 1 et 12 et `DD` est la valeur du jour qui est valide pour le mois donné `MM` .</span><span class="sxs-lookup"><span data-stu-id="16643-131">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="16643-132">La partie heure doit avoir le format : `HH`:`MM`[:`SS`[.fffffff]], où `HH` est la valeur des heures comprise entre 0 et 23 inclus, `MM` est la valeur des minutes comprise entre 0 et 59 inclus, `SS` est la valeur des secondes comprise entre 0 et 59 inclus, et fffffff est la valeur des fractions de seconde comprise entre 0 et 9999999.</span><span class="sxs-lookup"><span data-stu-id="16643-132">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="16643-133">Toutes les plages de valeurs sont inclusives.</span><span class="sxs-lookup"><span data-stu-id="16643-133">All value ranges are inclusive.</span></span> <span data-ttu-id="16643-134">Les fractions de secondes sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="16643-134">Fractional seconds are optional.</span></span> <span data-ttu-id="16643-135">Les secondes sont facultatives à moins que les fractions de secondes soient spécifiées ; auquel cas, les secondes sont requises.</span><span class="sxs-lookup"><span data-stu-id="16643-135">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="16643-136">Lorsque les secondes ou les fractions de secondes ne sont pas spécifiées, la valeur par défaut zéro est utilisée.</span><span class="sxs-lookup"><span data-stu-id="16643-136">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="16643-137">Le symbole DATETIME et la charge utile du littéral peuvent être séparés d'autant d'espaces que nécessaire, mais pas de nouvelles lignes.</span><span class="sxs-lookup"><span data-stu-id="16643-137">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="16643-138">Temps</span><span class="sxs-lookup"><span data-stu-id="16643-138">Time</span></span>  

 <span data-ttu-id="16643-139">Un littéral d'heure (time) est indépendant des paramètres régionaux. Il n'est composé que d'une partie heure.</span><span class="sxs-lookup"><span data-stu-id="16643-139">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="16643-140">La partie heure est obligatoire et n'est assortie d'aucune valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="16643-140">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="16643-141">Elle doit respecter le format HH:MM[:SS[.fffffff]], où HH est la valeur des heures comprise entre 0 et 23 inclus, MM est la valeur des minutes comprise entre 0 et 59 inclus, SS est la valeur des secondes comprise entre 0 et 59 inclus, et fffffff est la valeur des fractions de seconde comprise entre 0 et 9999999 inclus.</span><span class="sxs-lookup"><span data-stu-id="16643-141">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="16643-142">Toutes les plages de valeurs sont inclusives.</span><span class="sxs-lookup"><span data-stu-id="16643-142">All value ranges are inclusive.</span></span> <span data-ttu-id="16643-143">Les fractions de secondes sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="16643-143">Fractional seconds are optional.</span></span> <span data-ttu-id="16643-144">Les secondes sont facultatives à moins que les fractions de secondes soient spécifiées ; auquel cas, les secondes sont requises.</span><span class="sxs-lookup"><span data-stu-id="16643-144">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="16643-145">Lorsque les secondes ou les fractions de secondes ne sont pas spécifiées, la valeur par défaut zéro est utilisée.</span><span class="sxs-lookup"><span data-stu-id="16643-145">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="16643-146">Le symbole TIME et la charge utile du littéral peuvent être séparés d'autant d'espaces que nécessaire, mais pas de nouvelles lignes.</span><span class="sxs-lookup"><span data-stu-id="16643-146">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="16643-147">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="16643-147">DateTimeOffset</span></span>  

 <span data-ttu-id="16643-148">Un littéral datetimeoffset est indépendant des paramètres régionaux. Il est composé d'une partie date, d'une partie heure et d'une partie décalage.</span><span class="sxs-lookup"><span data-stu-id="16643-148">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="16643-149">Toutes ces parties sont obligatoires et il n'existe pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="16643-149">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="16643-150">La partie date doit respecter le format YYYY-MM-DD, où YYYY est une année à quatre chiffres comprise entre 0001 et 9999, MM est une valeur comprise entre 1 et 12 qui représente le mois et DD est la valeur du jour valide pour le mois donné.</span><span class="sxs-lookup"><span data-stu-id="16643-150">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="16643-151">La partir heure doit respecter le format HH:MM[:SS[.fffffff]], où HH est la valeur des heures comprise entre 0 et 23 inclus, MM est la valeur des minutes comprise entre 0 et 59 inclus, SS est la valeur des secondes comprise entre 0 et 59 inclus, et fffffff est la valeur des fractions de seconde comprise entre 0 et 9999999 inclus.</span><span class="sxs-lookup"><span data-stu-id="16643-151">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="16643-152">Toutes les plages de valeurs sont inclusives.</span><span class="sxs-lookup"><span data-stu-id="16643-152">All value ranges are inclusive.</span></span> <span data-ttu-id="16643-153">Les fractions de secondes sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="16643-153">Fractional seconds are optional.</span></span> <span data-ttu-id="16643-154">Les secondes sont facultatives à moins que les fractions de secondes soient spécifiées ; auquel cas, les secondes sont requises.</span><span class="sxs-lookup"><span data-stu-id="16643-154">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="16643-155">Lorsque les secondes ou les fractions de secondes ne sont pas spécifiées, la valeur par défaut zéro est utilisée.</span><span class="sxs-lookup"><span data-stu-id="16643-155">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="16643-156">La partie de décalage doit avoir le format {+&#124;-} HH : MM, où HH et MM ont la même signification que dans la partie heure.</span><span class="sxs-lookup"><span data-stu-id="16643-156">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="16643-157">Toutefois, la plage du décalage doit être comprise entre -14:00 et +14:00.</span><span class="sxs-lookup"><span data-stu-id="16643-157">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="16643-158">Le symbole DATETIMEOFFSET et la charge utile du littéral peuvent être séparés d'autant d'espaces que nécessaire, mais pas de nouvelles lignes.</span><span class="sxs-lookup"><span data-stu-id="16643-158">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
> <span data-ttu-id="16643-159">Une valeur littérale Entity SQL valide peut se situer hors des plages prises en charge pour CLR ou la source de données.</span><span class="sxs-lookup"><span data-stu-id="16643-159">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="16643-160">Cela peut donner lieu à une exception.</span><span class="sxs-lookup"><span data-stu-id="16643-160">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="16643-161">Binary</span><span class="sxs-lookup"><span data-stu-id="16643-161">Binary</span></span>  

 <span data-ttu-id="16643-162">Un littéral de chaîne binaire (binary) est une séquence de chiffres hexadécimaux délimitée par des guillemets simples à la suite du mot clé binary ou du symbole de raccourci `X` ou `x`.</span><span class="sxs-lookup"><span data-stu-id="16643-162">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="16643-163">Le symbole de raccourci `X` ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="16643-163">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="16643-164">Notez que les espaces sont autorisés entre le mot clé `binary` et la valeur de chaîne binaire.</span><span class="sxs-lookup"><span data-stu-id="16643-164">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="16643-165">Les caractères hexadécimaux ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="16643-165">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="16643-166">Si le littéral est composé d'un nombre impair de chiffres hexadécimaux, un chiffre zéro hexadécimal lui sera ajouté en préfixe pour permettre son alignement sur le prochain chiffre hexadécimal pair.</span><span class="sxs-lookup"><span data-stu-id="16643-166">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="16643-167">Il n'existe pas de limite formelle relativement à la taille de la chaîne binaire.</span><span class="sxs-lookup"><span data-stu-id="16643-167">There is no formal limit on the size of the binary string.</span></span>  
  
```sql  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="16643-168">Guid</span><span class="sxs-lookup"><span data-stu-id="16643-168">Guid</span></span>  

 <span data-ttu-id="16643-169">Un littéral `GUID` représente un identificateur global unique.</span><span class="sxs-lookup"><span data-stu-id="16643-169">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="16643-170">Il s’agit d’une séquence formée par le mot clé `GUID` suivi de chiffres hexadécimaux sous la forme « format de *registre* : 8-4-4-4-12 » entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="16643-170">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="16643-171">Les chiffres hexadécimaux ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="16643-171">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="16643-172">Le symbole GUID et la charge utile du littéral peuvent être séparés d'autant d'espaces que nécessaire, mais pas de nouvelles lignes.</span><span class="sxs-lookup"><span data-stu-id="16643-172">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```sql  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="16643-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16643-173">See also</span></span>

- [<span data-ttu-id="16643-174">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="16643-174">Entity SQL Overview</span></span>](entity-sql-overview.md)
