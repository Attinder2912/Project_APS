<template>
    <h3>Add New Transaction</h3>
    <form id="form">
        <div class="form-control">
            <label for="text">Text</label>
            <input type="text" id="text" placeholder="Enter text...">
        </div>
        <div class="form-control">
            <lablel for="amount">Amount<br/>(Negative - expense, postitve -income)</lablel>
            <input type="number" id="amount" placeholder="Enter amount...">
        </div>
        <button class="btn">Add transaction</button>
    </form>
</template>