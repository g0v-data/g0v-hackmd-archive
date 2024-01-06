<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE machine[
    <!ELEMENT machine (cultivator+)>
    <!ELEMENT cultivator (brand,model,hp,color+,weight?,tire)>
    <!ELEMENT brand (#PCDATA)>
    <!ELEMENT model (#PCDATA)>
    <!ELEMENT hp (#PCDATA)>
    <!ELEMENT color (#PCDATA)>
    <!ELEMENT weight (#PCDATA)>
    <!ELEMENT tire (#PCDATA)>
    
    <!ATTLIST brand country CDATA #REQUIRED>
]>

<machine>

<cultivator>
    <brand country='日本'>野馬</brand>
    <model>AF220</model>
    <color>red</color>
    <hp>22</hp>
    <tire>four</tire>
</cultivator>

<cultivator>
    <brand country="臺灣">大農</brand>
    <model>TSA-220</model>
    <color>green</color>
    <color>red</color>
    <hp>19</hp>
    <weight>550kg</weight>
    <tire>four</tire>
</cultivator>

<cultivator>
    <brand country='日本'>井關</brand>
    <model>TJV75</model>
    <color>blue</color>
    <hp>75</hp>
    <tire>four</tire>
</cultivator>

</machine>


