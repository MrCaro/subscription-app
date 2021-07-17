<template>
    <div class="container mx-auto">       
        <div class="w-full">
            <ul class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 gap-x-16 ">
                <li 
                    class="bg-grey-200 opacity-50 rounded-lg p-5 text-gray-100 shadow-2xl mb-16"
                    v-for="(subscription, index) in json" 
                    :key="index"
                >
                    <div class="flex">
                        <div class="w-3/12">
                            <img 
                                class="aspect-w-1 aspect-h-1 object-fit"
                                :class="subscription.status ? '' : 'opacity-50'"
                                :srcset="subscription.img"
                                :src="subscription.img" 
                                :alt="subscription.name"
                            >
                        </div>
                        <div class="w-9/12">
                            <div class="flex flex-col items-start">
                                <div class="flex justify-between w-full">
                                    <p 
                                        class="font-mono capitalize"
                                        v-if="subscription.price !== undefined" 
                                    >
                                        {{ subscription.name }}
                                    </p>
                                    <span
                                        class="font-sans text-sm border-2 rounded-full px-2"
                                        :class="subscription.status ? 'text-green-500 border-green-500' : 'text-red-500 border-red-500'"
                                        v-if="subscription.status !== undefined" 
                                    >
                                        {{ subscription.status ? 'active' : 'cancelled' }}
                                    </span>
                                </div>
                                <p 
                                    class="font-sans"
                                    :class="subscription.status ? '' : 'line-through'"
                                    v-if="subscription.price !== undefined" 
                                >
                                    <strong>
                                        <span class="text-lg text-grey-900">${{ subscription.price }}/</span><span class="text-sm">month</span>
                                    </strong>
                                </p>
                                <div class="flex justify-between w-full">
                                    <p
                                        class="font-sans text-sm"
                                        :class="subscription.status ? '' : 'line-through'"
                                        v-if="subscription.date != undefined"
                                    >
                                        payment on <strong>{{ subscription.date }}</strong>
                                    </p>
                                    <a
                                        class="font-sans transition duration-500 hover:opacity-50 underline"
                                        v-if="subscription.price !== undefined"
                                        :href="subscription.link"
                                    >
                                        visit site
                                    </a>
                                </div>
                            </div>
                        </div>
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
    import subscriptionsJson from '../assets/data/subscriptions.json'
    export default {
        name: 'Cards',
        props: {
            msg: String
        },
        data() {
            return {
                json: subscriptionsJson
            }
        },
        methods: {
            test() {
                console.log('hello there')
            }
        }
    }
</script>