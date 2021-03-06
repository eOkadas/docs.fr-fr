---
title: LINQ et chaînes (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: c7a1b86cc611d5f38ceab814b4594f5ad953fbc4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744620"
---
# <a name="linq-and-strings-c"></a>LINQ et chaînes (C#)

LINQ peut être utilisé pour interroger et transformer des chaînes et des collections de chaînes. Il peut être particulièrement utile avec des données semi-structurées dans des fichiers texte. Les requêtes LINQ peuvent être combinées avec les fonctions de chaîne traditionnelles et les expressions régulières. Par exemple, vous pouvez utiliser la méthode <xref:System.String.Split%2A?displayProperty=nameWithType> ou <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> pour créer un tableau de chaînes que vous pouvez ensuite interroger ou modifier à l’aide de LINQ. Vous pouvez utiliser la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> dans la clause `where` d’une requête LINQ. Et vous pouvez utiliser LINQ pour interroger ou modifier les résultats <xref:System.Text.RegularExpressions.MatchCollection> retournés par une expression régulière.

Vous pouvez également utiliser les techniques décrites dans cette section pour transformer des données texte semi-structurées en XML. Pour plus d'informations, voir [Procédure : Générer du code XML à partir de fichiers CSV](how-to-generate-xml-from-csv-files.md).

Les exemples de cette section se répartissent en deux catégories :

## <a name="querying-a-block-of-text"></a>Interrogation d’un bloc de texte

Vous pouvez interroger, analyser et modifier des blocs de texte en les fractionnant en tableau requêtable de chaînes plus petites à l’aide de la méthode <xref:System.String.Split%2A?displayProperty=nameWithType> ou de la méthode <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>. Vous pouvez fractionner le texte source en mots, en phrases, en paragraphes, en pages ou selon d’autres critères, puis effectuer des fractionnements supplémentaires s’ils sont nécessaires dans votre requête.

- [Guide pratique pour compter les occurrences d’un mot dans une chaîne (LINQ) (C#)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Montre comment utiliser LINQ pour des interrogations simples sur du texte.

- [Guide pratique pour rechercher des phrases qui contiennent un groupe de mots spécifié (LINQ) (C#)](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Montre comment fractionner des fichiers texte avec des limites arbitraires et comment exécuter des requêtes sur chaque partie.

- [Guide pratique pour rechercher des caractères dans une chaîne (LINQ) (C#)](how-to-query-for-characters-in-a-string-linq.md)

  Montre qu’une chaîne est un type interrogeable.

- [Guide pratique pour combiner des requêtes LINQ avec des expressions régulières (C#)](how-to-combine-linq-queries-with-regular-expressions.md)

  Montre comment utiliser des expressions régulières dans les requêtes LINQ pour des correspondances de modèle complexes sur des résultats de requête filtrés.

## <a name="querying-semi-structured-data-in-text-format"></a>Interrogation de données semi-structurées au format texte

De nombreux types différents de fichiers texte sont constitués d’une série de lignes, souvent avec la même mise en forme, comme les fichiers délimités par des tabulations ou des virgules, ou des lignes de longueur fixe. Après avoir lu un tel fichier texte dans la mémoire, vous pouvez utiliser LINQ pour interroger et/ou modifier les lignes. Les requêtes LINQ simplifient également la combinaison de données provenant de plusieurs sources.

- [Guide pratique pour rechercher la différence ensembliste entre deux listes (LINQ) (C#)](how-to-find-the-set-difference-between-two-lists-linq.md)

  Montre comment rechercher toutes les chaînes qui sont présentes dans une liste mais pas dans l’autre.

- [Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Montre comment trier les lignes de texte en fonction de n’importe quel mot ou champ.

- [Guide pratique pour réorganiser les champs d’un fichier délimité (LINQ) (C#)](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  Montre comment réorganiser les champs dans une ligne d’un fichier .csv.

- [Guide pratique pour combiner et comparer des collections de chaînes (LINQ) (C#)](how-to-combine-and-compare-string-collections-linq.md)

  Montre comment combiner des listes de chaînes de différentes façons.

- [Guide pratique pour remplir des collections d’objets issues de plusieurs sources (LINQ) (C#)](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Montre comment créer des collections d’objets à l’aide de plusieurs fichiers texte comme sources de données.

- [Guide pratique pour joindre du contenu issu de fichiers non similaires (LINQ) (C#)](how-to-join-content-from-dissimilar-files-linq.md)
  
  Montre comment combiner des chaînes de deux listes en une seule chaîne en utilisant une clé en correspondance.

- [Guide pratique pour fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (C#)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Montre comment créer des fichiers en utilisant un seul fichier comme source de données.

- [Guide pratique pour calculer des valeurs de colonnes dans un fichier texte CSV (LINQ) (C#)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  Montre comment effectuer des calculs mathématiques sur des données texte dans des fichiers .csv.

## <a name="see-also"></a>Voir aussi

- [LINQ (Language-Integrated Query) (C#)](index.md)
- [Guide pratique pour générer du code XML à partir de fichiers CSV](how-to-generate-xml-from-csv-files.md)
