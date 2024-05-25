def les_premiers_pays(t_pays):
    # Variables pour suivre les meilleurs pays dans chaque catégorie
    max_or = []
    max_argent = []
    max_bronze = []
    max_total = []
    max_valeur = []

    max_or_count = max_argent_count = max_bronze_count = -1
    max_total_count = max_valeur_points = -1

    for pays in t_pays:
        or_, argent, bronze = pays.medailles
        total_medals = or_ + argent + bronze
        valeur_medals = 3 * or_ + 2 * argent + 1 * bronze

        # Vérifier et mettre à jour les pays avec le plus de médailles d'or
        if or_ > max_or_count:
            max_or = [pays]
            max_or_count = or_
        elif or_ == max_or_count:
            max_or.append(pays)

        # Vérifier et mettre à jour les pays avec le plus de médailles d'argent
        if argent > max_argent_count:
            max_argent = [pays]
            max_argent_count = argent
        elif argent == max_argent_count:
            max_argent.append(pays)

        # Vérifier et mettre à jour les pays avec le plus de médailles de bronze
        if bronze > max_bronze_count:
            max_bronze = [pays]
            max_bronze_count = bronze
        elif bronze == max_bronze_count:
            max_bronze.append(pays)

        # Vérifier et mettre à jour les pays avec le plus de médailles au total
        if total_medals > max_total_count:
            max_total = [pays]
            max_total_count = total_medals
        elif total_medals == max_total_count:
            max_total.append(pays)

        # Vérifier et mettre à jour les pays avec la plus grande valeur des médailles
        if valeur_medals > max_valeur_points:
            max_valeur = [pays]
            max_valeur_points = valeur_medals
        elif valeur_medals == max_valeur_points:
            max_valeur.append(pays)

    # Fonction d'affichage des résultats
    def afficher_premiers(premiers, categorie):
        noms = ", ".join(p.nom for p in premiers)
        print(f"Premier pays en nb médailles {categorie} : {noms}, or : {premiers[0].medailles[0]}, argent : {premiers[0].medailles[1]}, bronze : {premiers[0].medailles[2]}")

    # Affichage des résultats pour chaque catégorie
    afficher_premiers(max_or, "or")
    afficher_premiers(max_argent, "argent")
    afficher_premiers(max_bronze, "bronze")
    afficher_premiers(max_total, "total")
    afficher_premiers(max_valeur, "valeur des médailles")
