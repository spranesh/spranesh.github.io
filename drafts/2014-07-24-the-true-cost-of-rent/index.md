# The true cost of renting


<script type="text/javascript">

function GetBonusMessage(extra) {
     var item = "";
     if( extra > 150000 )
        item = "a european vacation";
     else if( extra > 100000 )
        item = "a used hatchback";
     else if( extra > 70000 )
        item = "a very good two wheeler";
     else if( extra > 50000 )
        item = "a home theatre system";
     else if ( extra > 40000 )
        item = "the best camera phone that currently exists";
     else if ( extra > 30000 )
        item = "a top choice entry-level DSLR camera";
     else if ( extra > 20000 )
        item = "a top of the line smartphone";
     else if ( extra > 10000 )
        item = "a fairly good smartphone";
     else if ( extra > 5000 )
        item = "return tickets for a domestic flight (if you book early)";
     else if ( extra > 2000 )
        item = "a spa package";

     if ( item != "" )
     {
        var bonus_msg = "<b>Bonus</b>: To put that in perspective, the amount you would save during your whole tenure, ";
        bonus_msg    += "Rs. <span class=net-extra-for-tenure></span> could buy you " + item +"."; 
        return bonus_msg;
     }
     return "";
}

function CalculateTrueCost() {
     $( "#analysis" ).hide();


     var interest      = 0.06;

     var broker_months = 1.0 * ( $( "#broker-used" ).is(":checked") ? 1 : 0 );
     var tenure          = parseFloat( $( "#months-rented" ).val() );
     var advance         = parseFloat( $( "#months-advance" ).val() );
     var painting_charge = parseFloat( $( "#painting-charges" ).val() );
     var monthly_rent    = parseFloat( $( "#monthly-rent" ).val() );

     $( ".tenure" ).html( tenure.toFixed( 1 ) );

     var broker_charge 	       = broker_months * monthly_rent;
     var deposit_interest      = monthly_rent * tenure / 12 * advance * interest;
     var net_extra_for_tenure  = broker_charge + deposit_interest + painting_charge;
     var net_extra_per_month   = net_extra_for_tenure / tenure;
     var net_extra_percentage  = net_extra_per_month / monthly_rent * 100;

     // display Bonus first to fill in numbers inside the bonus.
     $( "#bonus" ).html( GetBonusMessage( net_extra_for_tenure ) );

     $( ".deposit-interest" ).html( deposit_interest.toFixed( 0 ));
     $( ".painting-charge" ).html( painting_charge.toFixed( 0 ) );
     $( ".broker-charge" ).html( broker_charge.toFixed( 0 ) );
     $( ".painting-broker" ).html( (painting_charge + broker_charge ).toFixed( 0 ) );

     $( ".net-extra-for-tenure" ).html( net_extra_for_tenure.toFixed( 0 ) );
     $( ".net-extra-percentage" ).html( net_extra_percentage.toFixed( 2 ) );
     $( ".net-extra-per-month" ).html( net_extra_per_month.toFixed(0) );
     $( ".true-rent" ).html( ( net_extra_per_month + monthly_rent ).toFixed( 0 ) );

     $( "#analysis" ).show( "slow" );
      return false;
};
</script>

Ever since I read about [the true cost of owning a
car](http://www.investopedia.com/articles/pf/08/cost-car-ownership.asp), I've
generally thought about the true all-in costs of things -- a phone plan, a
housing loan, running a hypothetical _chai_ shop, etc.. While I pursue this
train of thought for purely intellectual purposes, it sometimes leads to
conclusions that I find surprising.

The most recent one for me was the true cost of renting an apartment in
Bangalore -- given the many (6-10) months deposit required, the post-lease
maintenance clauses, and the prevalent brokerage charges.  However, unlike the
case of a car, there is no viable alternative to renting. Still, it makes for
an interesting calculation.

Anyhow, the point is the actual rent paid (and received by the owner in some
form or the other) is very different from the "advertised rent" due to the
above factors. Here's a calculator I built to calculate the _true_ cost of
rent.  I've set default values that I think are representative of what I have
personally observed and heard about. In my current case for instance, the
_true_ cost of renting comes to 18% more than advertised:

<!--[^1]: As an aside, given these numbers and the default 30% maintenance
waiver the government gives on the _advertised_ rent, it's even more
astonishing to think about the low net tax rate from rental income.  Even in
the highest 30% tax bracket, the owner pays tax only on every 70 rupees he/she
gets for every 100 advertised and 120 true / real rupees of income. This brings
the tax paid to Rs 21 and the net effective tax to a mere 17.5%. Of course,
this is still high compared to not paying taxes at all (as the trend is these
days).-->

<form id="calc-form" class="form-horizontal col-md-offset-3" role="form"
onsubmit="javascript: return CalculateTrueCost()">

  <div class="form-group">
    <label for="rent" class="col-sm-7">Monthly Rent</label>
    <input type="text" class="col-sm-3" id="monthly-rent" value="20000">
  </div>

  <div class="form-group">
    <label for="months-rented" class="col-sm-7">Number of months rented</label>
    <input type="text" class="col-sm-3" id="months-rented" value="11">
  </div>

  <div class="form-group">
    <label for="months-advance" class="col-sm-7">Deposit Advance (in months)</label>
    <input type="text" class="col-sm-3" id="months-advance" value="8">
  </div>

  <div class="form-group">
    <label for="painting-charges" class="col-sm-7">Painting charges in rupees</label>
    <input type="text" class="col-sm-3" id="painting-charges" value="15000">
  </div>

  <div class="form-group">
    <label for="broker-used" class="col-sm-7">Found via broker</label>
    <input type="checkbox" class="col-sm-1" id="broker-used" checked>
  </div>

  <div class="form-group">
    <div class="col-sm-2">
      <button type="submit" class="btn btn-primary">Calculate True Cost of Rent</button>
    </div>
  </div>
</form>


<div id="analysis" style="display:none">
<br />

<p><b>Summary:</b> You are paying an extra Rs. <span
class="net-extra-per-month"></span>(<span
class="net-extra-percentage"></span>%) extra per month for a total <i>true</i>
rent of Rs. <span class="true-rent"></span> per month. Over your tenure, the
extra amount you are paying above your stated rent is Rs. <span
class="net-extra-for-tenure"></span>:</p>

<ol> <li>
Assuming a risk free interest of 6% (say via fixed deposit) after taxes, you
would have earnt Rs. <span class="deposit-interest"></span> over your tenure of
<span class="tenure"></span> months had you kept the deposit interest to your
self.  

</li> <li> The re-painting charge of Rs. <span class="painting-charge"></span>
and a broker charge of Rs. <span class="broker-charge"></span> added together
comes to Rs.  <span class="painting-broker"></span>, your fixed costs of rent
for your tenure.

</li><li> Adding the above two items together, the net cost is Rs.<span
class="net-extra-for-tenure"></span>. Amortizing this over your stay of <span
class="tenure"></span> months, this results in paying Rs. <span
class="net-extra-per-month"></span> extra per month.  Note that this analysis
assumes you have managed to obtain your original deposit amount back when you
leave from your landlord and that you are not breaking the lease. </p> </li>
</ol>

<br />

<small><div id="bonus"></div></small>

<br />

</div>

Of course, given the sky high rental demand, the inherent power asymmetry, and
the need for a roof over our heads, this is merely an intellectual exercise for
most of us.

