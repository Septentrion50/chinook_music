# Réponses aux questions de l'exercice 2.2.3

| num | Commande | Réponse (quand possible) |
|:----:|:----|:----|
|1| `Album.all.size` | 347 |
|2| `Track.find_by(title: "White Room").artist` | Eric Clapton |
|3| `Track.find_by(duration: 188133).title` | Perfect |
|4| `Album.find_by(title: "Use Your Illusion II").artist` | Guns N Roses |
|5| `Album.where("title LIKE ?", "%Great%").size` | 13 |
|6| `Album.where("title LIKE ?", "%music%").destroy_all` | Il y en avait 4 |
|7| `Album.where("artist = ?", "AC/DC").size` | 2 |
|8| `Track.where("duration = ?", 158589).size` | 0 |

## Boucles

**N°9**

```rb
Track.where("artist = ?", "AC/DC").each do |t|
  puts t.title
end 
=begin
For Those About To Rock (We Salute You)
Put The Finger On You
Lets Get It Up
Inject The Venom
Snowballed
Evil Walks
C.O.D.
Breaking The Rules
Night Of The Long Knives
Spellbound
Go Down
Dog Eat Dog
Let There Be Rock
Bad Boy Boogie
Problem Child
Overdose
Hell Aint A Bad Place To Be
Whole Lotta Rosie
=end
```

**N°10**

```rb
Track.where("album = ?", "Let There Be Rock").each do |t|
  puts t.title
end
=begin
Go Down
Dog Eat Dog
Let There Be Rock
Bad Boy Boogie
Problem Child
Overdose
Hell Aint A Bad Place To Be
Whole Lotta Rosie
=end
```

**N°11**

```rb
al_price = 0
al_dur = 0
Track.where("album = ?", "Let There Be Rock").each do |t|
  puts "prix : #{al_price += t.price}"
  puts "durée : #{al_dur += t.duration}"
end
=begin
prix : 0.99
durée : 331180
prix : 1.98
durée : 546376
prix : 2.9699999999999998
durée : 913030
prix : 3.96
durée : 1180758
prix : 4.95
durée : 1505799
prix : 5.94
durée : 1875118
prix : 6.930000000000001
durée : 2129498
prix : 7.920000000000001
durée : 2453259
=end

# Je fais des puts parce que dans la console c'est compliqué avec mon système.
```

**N°12**

```rb
deep_purple_cost = 0
Track.where("artist = ?", "Deep Purple").each do |t|
  puts deep_purple_cost += t.price
end
=begin
Je n'affiche que la dernière ligne des puts,
c'est celle qui nous intéresse :

180.18000000000018
=end
```

**N°13**

```rb
Track.where("artist = ?", "Eric Clapton").each do |t|
  t.update(artist: "Britney Spears")
end
=begin
Je me sens sale
=end
```

