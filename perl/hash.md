<!-- TITLE: Hashes -->

# Creating and displaying


```perl
my %valores = ();
my $test;
my $table;
my $tbl_base;
    
#Creating
foreach my $r (@ { $data }) {
    $test = $r->{'test'};
    $table = $r->{'table'};
    $tbl_base = $r->{'tbl_base'};
    $valores{$test}{$tbl_base}{$table}{'platform'} = $r->{'platform'};
    $valores{$test}{$tbl_base}{$table}{'description'} = $r->{'description'};
}

#Diplaying
foreach my $key (keys %valores)
{
    print "$key";
    for my $key2 (keys %{$valores{$key}})
    {
        print "$key2";
        for my $key3 (reverse sort(keys %{$valores{$key}{$key2}})){
            
            print "$key3";
            
            for my $key4 (keys %{$valores{$key}{$key2}{$key3}})
            { 
                print $key4;
                print $valores{$key}{$key2}{$key3}{$key4};
            }
            
        }
    }        
}

```
