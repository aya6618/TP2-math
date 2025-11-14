def pgcd(a, b):
    """Calcule le PGCD de a et b avec l'algorithme d'Euclide"""
    while b != 0:
        a, b = b, a % b
    return a

def euclide_etendu(a, b):
    """Algorithme d'Euclide étendu - retourne (d, x0, y0) tels que ax0 + by0 = d"""
    if b == 0:
        return a, 1, 0
    else:
        d, x1, y1 = euclide_etendu(b, a % b)
        x0 = y1
        y0 = x1 - (a // b) * y1
        return d, x0, y0

def resoudre_diophantienne(a, b, c):
    """Résout l'équation diophantienne ax + by = c"""
    # Étape 1: Calcul du PGCD et vérification
    d = pgcd(a, b)
    
    if c % d != 0:
        return None, None, None, None, d
    
    # Étape 2: Solution particulière avec Euclide étendu
    d, x0, y0 = euclide_etendu(a, b)
    
    # Ajustement pour c
    k = c // d
    xp = x0 * k
    yp = y0 * k
    
    # Étape 3: Forme générale des solutions
    alpha = b // d
    beta = -a // d
    
    return xp, yp, alpha, beta, d

# Interaction avec l'utilisateur
print("Résolution de l'équation diophantienne ax + by = c")
print("=" * 50)

try:
    a = int(input("Entrez la valeur de a : "))
    b = int(input("Entrez la valeur de b : "))
    c = int(input("Entrez la valeur de c : "))
    
    xp, yp, alpha, beta, d = resoudre_diophantienne(a, b, c)
    
    print("\n" + "=" * 50)
    print(f"Équation : {a}x + {b}y = {c}")
    print(f"PGCD({a}, {b}) = {d}")
    
    if xp is None:
        print(f" Pas de solution entière car {d} ne divise pas {c}")
    else:
        print(f" Il existe des solutions entières")
        print(f"Solution particulière : (xₚ, yₚ) = ({xp}, {yp})")
        print(f"Forme générale des solutions :")
        print(f"(x, y) = ({xp} + {alpha}k, {yp} + {beta}k), k ∈ ℤ")
        
        # Vérification
        print(f"\nVérification :")
        print(f"{a}×{xp} + {b}×{yp} = {a*xp + b*yp} = {c}")
        
except ValueError:
    print("Erreur : Veuillez entrer des nombres entiers valides")
except Exception as e:
    print(f"Erreur : {e}")