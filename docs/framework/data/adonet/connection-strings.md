---
title: Chaînes de connexion dans ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: bf053c7c26435bea5b2368c81c89b73e8949b74a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040137"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="3729e-102">Chaînes de connexion dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3729e-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="3729e-103">Une chaîne de connexion contient des informations d'initialisation qui sont passées en tant que paramètre d'un fournisseur de données à une source de données.</span><span class="sxs-lookup"><span data-stu-id="3729e-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="3729e-104">Le fournisseur de données reçoit la chaîne de connexion en tant que valeur de la propriété <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3729e-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="3729e-105">Le fournisseur analyse la chaîne de connexion et s’assure que la syntaxe est correcte et que les mots clés sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3729e-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="3729e-106">Ensuite, la méthode <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> transmet les paramètres de connexion analysés à la source de données.</span><span class="sxs-lookup"><span data-stu-id="3729e-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="3729e-107">La source de données effectue une validation supplémentaire et établit une connexion.</span><span class="sxs-lookup"><span data-stu-id="3729e-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="3729e-108">Syntaxe de chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="3729e-108">Connection string syntax</span></span>

<span data-ttu-id="3729e-109">Une chaîne de connexion est une liste délimitée par des points-virgules de paires de paramètres clé/valeur :</span><span class="sxs-lookup"><span data-stu-id="3729e-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>

```csharp
keyword1=value; keyword2=value;
```

<span data-ttu-id="3729e-110">Les mots clés ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="3729e-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="3729e-111">Toutefois, les valeurs peuvent respecter la casse, en fonction de la source de données.</span><span class="sxs-lookup"><span data-stu-id="3729e-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="3729e-112">Les mots clés et les valeurs peuvent contenir des [espaces blancs](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span><span class="sxs-lookup"><span data-stu-id="3729e-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="3729e-113">Les espaces blancs de début et de fin sont ignorés dans les mots clés et les valeurs sans guillemets.</span><span class="sxs-lookup"><span data-stu-id="3729e-113">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="3729e-114">Si une valeur contient le point-virgule, les [caractères de contrôle Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters)ou les espaces blancs de début ou de fin, elle doit être placée entre guillemets simples ou doubles.</span><span class="sxs-lookup"><span data-stu-id="3729e-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="3729e-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3729e-115">For example:</span></span>

```csharp
Keyword=" whitespace  ";
Keyword='special;character';
```

<span data-ttu-id="3729e-116">Le caractère englobant peut ne pas se trouver dans la valeur qu’il englobe.</span><span class="sxs-lookup"><span data-stu-id="3729e-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="3729e-117">Par conséquent, une valeur contenant des guillemets simples peut être placée entre guillemets doubles, et vice versa :</span><span class="sxs-lookup"><span data-stu-id="3729e-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

```csharp
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

<span data-ttu-id="3729e-118">Vous pouvez également échapper le caractère englobant à l’aide de deux d’entre eux :</span><span class="sxs-lookup"><span data-stu-id="3729e-118">You can also escape the enclosing character by using two of them together:</span></span>

```csharp
Keyword="double""quotation";
Keyword='single''quotation';
```

<span data-ttu-id="3729e-119">Les guillemets eux-mêmes, ainsi que le signe égal, ne nécessitent pas d’échappement, donc les chaînes de connexion suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="3729e-119">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

```csharp
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

<span data-ttu-id="3729e-120">Étant donné que chaque valeur est lue jusqu’au point-virgule suivant ou jusqu’à la fin de la chaîne, la valeur dans le dernier exemple est `a=b=c`et le point-virgule final est facultatif.</span><span class="sxs-lookup"><span data-stu-id="3729e-120">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="3729e-121">Toutes les chaînes de connexion partagent la même syntaxe de base décrite ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="3729e-121">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="3729e-122">Toutefois, l’ensemble des mots clés reconnus dépend du fournisseur et a évolué au fil des années à partir des API antérieures telles que *ODBC*.</span><span class="sxs-lookup"><span data-stu-id="3729e-122">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="3729e-123">Le fournisseur de données *.NET Framework* pour *SQL Server* (`SqlClient`) prend en charge de nombreux mots clés d’anciennes API, mais il est généralement plus flexible et accepte des synonymes pour un grand nombre des mots clés de chaîne de connexion courants.</span><span class="sxs-lookup"><span data-stu-id="3729e-123">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="3729e-124">Les erreurs de frappe peuvent entraîner des erreurs.</span><span class="sxs-lookup"><span data-stu-id="3729e-124">Typing mistakes can cause errors.</span></span> <span data-ttu-id="3729e-125">Par exemple, `Integrated Security=true` est valide, mais `IntegratedSecurity=true` provoque une erreur.</span><span class="sxs-lookup"><span data-stu-id="3729e-125">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="3729e-126">Les chaînes de connexion construites manuellement au moment de l’exécution à partir d’une entrée utilisateur non validée sont vulnérables aux attaques par injection de chaîne et mettent en péril la sécurité au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="3729e-126">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="3729e-127">Pour résoudre ces problèmes, *ADO.NET* 2,0 a introduit les [générateurs de chaînes de connexion](connection-string-builders.md) pour chaque fournisseur de données *.NET Framework* .</span><span class="sxs-lookup"><span data-stu-id="3729e-127">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="3729e-128">Ces générateurs de chaînes de connexion exposent des paramètres en tant que propriétés fortement typées et permettent de valider la chaîne de connexion avant qu’elle ne soit envoyée à la source de données.</span><span class="sxs-lookup"><span data-stu-id="3729e-128">These connection string builders expose parameters as strongly-typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3729e-129">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3729e-129">In This Section</span></span>

<span data-ttu-id="3729e-130">[Générateurs de chaînes de connexion](connection-string-builders.md)</span><span class="sxs-lookup"><span data-stu-id="3729e-130">[Connection String Builders](connection-string-builders.md)</span></span>\
<span data-ttu-id="3729e-131">Montre comment utiliser les classes `ConnectionStringBuilder` pour générer des chaînes de connexion valides au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="3729e-131">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>

<span data-ttu-id="3729e-132">[Chaînes de connexion et fichiers de Configuration](connection-strings-and-configuration-files.md)</span><span class="sxs-lookup"><span data-stu-id="3729e-132">[Connection Strings and Configuration Files](connection-strings-and-configuration-files.md)</span></span>\
<span data-ttu-id="3729e-133">Montre comment stocker et extraire des chaînes de connexion dans des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="3729e-133">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>

<span data-ttu-id="3729e-134">[Syntaxe](connection-string-syntax.md) de la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="3729e-134">[Connection String Syntax](connection-string-syntax.md)</span></span>\
<span data-ttu-id="3729e-135">Décrit comment configurer des chaînes de connexion spécifiques au fournisseur pour `SqlClient`, `OracleClient`, `OleDb` et `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="3729e-135">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>

<span data-ttu-id="3729e-136">[Protection des informations de connexion](protecting-connection-information.md)</span><span class="sxs-lookup"><span data-stu-id="3729e-136">[Protecting Connection Information](protecting-connection-information.md)</span></span>\
<span data-ttu-id="3729e-137">Montre des techniques pour la protection des informations utilisées pour la connexion à une source de données.</span><span class="sxs-lookup"><span data-stu-id="3729e-137">Demonstrates techniques for protecting information used to connect to a data source.</span></span>

## <a name="see-also"></a><span data-ttu-id="3729e-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3729e-138">See also</span></span>

- [<span data-ttu-id="3729e-139">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="3729e-139">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)
- [<span data-ttu-id="3729e-140">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3729e-140">ADO.NET Overview</span></span>](ado-net-overview.md)
