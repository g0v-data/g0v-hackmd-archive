# Mini HW2


$(1)\ Psuedo\ code$ 
$(Rewrite\ the\ slide\  used\ in\ class: "Divide\text-and\text-Conquer3.pdf"p.33)$

$Closest-Pair(P)$
$1\ \ sort\ P\ by\ x\text-\ and\ y\text-coordinate\ and\ store\ in\ Px\ and\ Py$
$2\ \ //\ base\ case$
$3\ \ if\ |P|\ <=\ 3:\ brute\text-force\ finding\ closest\ pair\ and\ return\ it$
$4\ \ //\ Divide$
$5\ \ find\ a\ vertical\ line\ L\ s.t.\ both\ planes\ contain\ half\ of\ the\ points$
$6\ \ //\ Conquer$
$7\ \ left\text-pair,\ left\text-min\ =\ Closest\text-Pair(points\ in\ the\ left)$
$8\ \ right\text-pair,\ right\text-min\ =\ Closest\text-Pair(points\ in\ the\ right)$
$9\ \ //\ Combine$
$\mathbf{10\ \ 	if\ it\ is\ in\ the\ final\ combination,\ i.e.\ the\ intitial\ two\ half\ part:}$
$\mathbf{11\ \ \ \ \ \ \ \ \ we\ consider\ the\ seam\ S,\ namely\ the\ border\ by\ x\text-coordinate,\ doing\ the\ same\ operate\ with\ L}$
$12\ \ delta\ =\ min\{left\text-min,\ right\text-min\}$
$13\ \ remove\ points\ that\ are\ delta\ or\ more\ away\ from\ L\ \mathbf{(\&\ S\ in\ the\ final\ combination)}$
$14\ \ for\ point\ p_i\ in\ sorted\ candidates:compute\ distances\ with\ p_k,where\ k\in(i,8]$
$15\ \ update\ delta\ if\ a\ closer\ pair\ is\ found$
$16\ \ return\ the\ closest\ pair\ and\ its\ distance$

$(2)correctness$
$We\ can\ image\ that\ a\ cylinder\ is\ a\ rectangle\ curls\ up\ into\ 3D,\ and\ seal\ a\ pair\ of\ sides\ to\ connect\ two\ sides.$
$Rather\ than\ a\ rectangle,\ a\ cylinder\ has\ to\ consider\ that\ if\ any\ closest\ condition\ occurs\ near\ the\ seam.$
$However,\ we\ only\ need\ to\ consider\ it\ once,\ that's\ when\ the\ final\ combination.$
$If\ and\ only\ if\ there\ exists\ a\ closer\ pair\ across\ the\ seam,\ we\ need\ to\ modify\ the\ result.$

$(3)time complexity$
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6bbb57985b95ece18f22ee7777b07679)

