# TravelMate-AI-Powered-Personalized-Travel-Itinerary-Planner
TravelMate uses generative AI and ML to create personalized travel itineraries based on users' preferences, budget, and desired experiences, making travel planning a breeze.
import random

class TravelMate:
    def __init__(self):
        self.destinations = {
            'beach': ['Maui', 'Maldives', 'Cancun'],
            'mountain': ['Swiss Alps', 'Rocky Mountains', 'Himalayas'],
            'city': ['New York', 'Paris', 'Tokyo']
        }
        self.activities = {
            'adventure': ['hiking', 'skiing', 'surfing'],
            'cultural': ['museum visits', 'historical tours', 'art exhibitions'],
            'relaxation': ['spa days', 'beach lounging', 'wine tasting']
        }

    def get_destination(self, preference):
        if preference in self.destinations:
            return random.choice(self.destinations[preference])
        return None

    def get_activities(self, preference, num_activities=2):
        if preference in self.activities:
            return random.sample(self.activities[preference], num_activities)
        return None

    def create_itinerary(self, preferences):
        destination = self.get_destination(preferences['experience'])
        activities = self.get_activities(preferences['activity'], preferences['num_activities'])

        if destination and activities:
            itinerary = {
                'destination': destination,
                'activities': activities,
                'budget': preferences['budget']
            }
            return itinerary
        return "Sorry, we couldn't match your preferences with our options."

def main():
    user_preferences = {
        'experience': 'beach', # or 'mountain', 'city'
        'activity': 'adventure', # or 'cultural', 'relaxation'
        'num_activities': 2,
        'budget': '$1500-$2000'
    }

    travel_planner = TravelMate()
    itinerary = travel_planner.create_itinerary(user_preferences)
    print("Your personalized travel itinerary:", itinerary)

if __name__ == "__main__":
    main()
