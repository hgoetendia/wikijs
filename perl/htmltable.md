<!-- TITLE: Create Html table hash based-->

```perl
print "<table border='1' style='border-collapse:collapse;'>";

foreach my $key (keys %valores)
{
    print "<tr>";
    print "<td>";
    print "$key";
    print "</td>";

    print "<td>";
    print "<table border='1' width = '100%' style='border-collapse:collapse;'>";
    for my $key2 (keys %{$valores{$key}})
    {
        print "<tr>";
        print "<td>";
        print "$key2";
        print "</td>";
        print "<td>";
        print "<table border='0' width='100%' style='border-collapse:collapse;'>";

        for my $key3 (reverse sort(keys %{$valores{$key}{$key2}})){
            print  "<tr>";
            print  "<td>";
            print  "$key3";
            print  "</td>";
            print  "<td>";
            print  "<table border='0' width='100%' style='border-collapse:collapse;'>";
            
            for my $key4 (keys %{$valores{$key}{$key2}{$key3}})
            { 
                print  "<tr>";
                print  "<td>$key4</td>";
                
                if ( uc($key4) eq "STATUS" ){
                    if ($valores{$key}{$key2}{$key3}{$key4} eq "OK"){
                        print  "<td align='center' bgcolor='#00FF00'>";
                        print  "<font color='black'>";
                        print  "$valores{$key}{$key2}{$key3}{$key4}";
                        print  "</font>";
                        print  "</td>";                            
                    }
                    else{
                        print  "<td align='center' bgcolor='#FF0000'>$valores{$key}{$key2}{$key3}{$key4}</td>";
                    }
                }
                else{
                    print  "<td align='center'>$valores{$key}{$key2}{$key3}{$key4}</td>";
                }
                
                print  "</tr>";
                print  "";
            }
            
            print  "</table>";
            print  "</td>";
            print  "</tr>";
        }

        print "</table>";
        print "</td>";
        print "</tr>";
    }
    
    print "</table>";
    print "</td>";
    print "</tr>";    
}
print "</table>";
```

