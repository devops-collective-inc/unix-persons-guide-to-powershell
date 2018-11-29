# commands detail - r

## read -p

In \*nix:

~~~~~~~~
read -p "Which is the only London club to win the Champions League? " team
echo $team
~~~~~~~~
In Powershell:

~~~~~~~~
$team = read-host "Which is the only London club to win the Champions League?"
Which is the only London club to win the Champions League? : Chelsea

$team
Chelsea
~~~~~~~~

To _not_ echo the input to screen, you would do

~~~~~~~~
$SecretString = read-host "Whats your secret? "-assecurestring
~~~~~~~~

This echoes out an asterisk  for each character input


## rm

~~~~~~~~
Remove-Item
~~~~~~~~

