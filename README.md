THE TAP METHOD
==============
`2.3.0 :001 > journey_history = [{entry: "Queens Road Peckham", exit: "Aldgate East"}, {entry: "Aldgate East", exit: "Queens Road Peckham"}, {entry: "Queens Road Peckham", exit: "Aldgate East"}]`

 `=> [{:entry=>"Queens Road Peckham", :exit=>"Aldgate East"}, {:entry=>"Aldgate East", :exit=>"Queens Road Peckham"}, {:entry=>"Queens Road Peckham", :exit=>"Aldgate East"}] `

`2.3.0 :002 > journey = {entry: "Victoria", exit: "Highbury & Islington"}`

` => {:entry=>"Victoria", :exit=>"Highbury & Islington"} `

`2.3.0 :003 > journey_history.tap {|hist| hist << journey}`
 
` => [{:entry=>"Queens Road Peckham", :exit=>"Aldgate East"}, {:entry=>"Aldgate East", :exit=>"Queens Road Peckham"}, {:entry=>"Queens Road Peckham", :exit=>"Aldgate East"}, {:entry=>"Victoria", :exit=>"Highbury & Islington"}]`
